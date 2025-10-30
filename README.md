# EXP 1 : Linear and Circular Convolution

## AIM: 

 To perform Linear and Circular Convolution for two given sequence using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM (Linear Convolution): 

// Linear Convolution
```
clc;
clear;
x = input("Enter x(n):");
h = input("Enter h(n):");
Nx = length(x);
Nh = length(h);
Ny = Nx + Nh - 1;
x_p = [x, zeros(1, Ny - Nx)];
h_p = [h, zeros(1, Ny - Nh)];
y = zeros(1, Ny);
for n = 0:Ny-1
    for k = 0:Nx-1
        if (n-k >= 0 & n-k < Nh) then
            y(n+1) = y(n+1) + x_p(k+1) * h_p(n-k+1);
        end
    end
end
disp("y(n)"), disp(y);
clf;
subplot(3,1,1);
n1 = 0:Nx-1;
plot2d3(n1, x);
xtitle("x(n)");
subplot(3,1,2);
n2 = 0:Nh-1;
plot2d3(n2, h);
xtitle("h(n)");
subplot(3,1,3);
n3 = 0:Ny-1;
plot2d3(n3, y);
xtitle("y(n) = x(n) * h(n)");
```


## PROGRAM (Circular Convolution): 
```
clc;
clear;

x = [5 6 7 8];
h = [2 3 0 0];

N = max(length(x), length(h));

// Pad sequences to equal length
x = [x, zeros(1, N-length(x))];
h = [h, zeros(1, N-length(h))];

y = zeros(1, N);

// Circular convolution
for n = 1:N
    for m = 1:N
        k = n - m;
        if k < 0 then
            k = k + N; // wrap around
        end
        y(n) = y(n) + x(m) * h(k+1); // +1 for 1-based indexing
    end
end

disp("Circular Convolution Result:");
disp(y);

// Plotting the result
n = 0:N-1;           // x-axis indices
figure(0);            // create figure window
plot2d3(n, y);           // stem plot
xlabel("n");          
ylabel("y(n)");
title("Circular Convolution of x(n) and h(n)");
               // show grid
```
// Circular Convolution

## OUTPUT (Linear Convolution): 
<img width="1300" height="633" alt="image" src="https://github.com/user-attachments/assets/ee1df746-425a-432e-bf29-f5942c5c538c" />


## OUTPUT (Circular Convolution): 
<img width="1187" height="685" alt="image" src="https://github.com/user-attachments/assets/a08b9964-1bec-44dc-a9f1-4e270e4eb641" />


## RESULT: 
Linear and Circular Convolution for two given sequence using SCILAB was performed.
