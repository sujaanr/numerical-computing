# Newton-Raphson Method in Julia

This repository contains Julia code implementing the Newton-Raphson method to find the root of a given function.

## Overview

The Newton-Raphson method is an iterative root-finding algorithm that uses linear approximation to find successively better approximations to the roots (or zeroes) of a real-valued function. It is particularly useful for finding the roots of differentiable functions.

## Usage
Replace the function f(x) with your desired function. Adjust the initial guess (x0), tolerance (tolerance), and maximum number of iterations (max_iterations) as needed for your problem.

### Function Definition

```julia
# Define the derivative of the function
function df(x)
    return 3x^2 - 4x
end

# Implement Newton-Raphson method
function newton_raphson(f, df, x0, tol, max_iter)
    x = x0
    iter = 0
    while abs(f(x)) > tol && iter < max_iter
        x -= f(x) / df(x)
        iter += 1
    end
    if abs(f(x)) <= tol
        println("Root found at x = ", x, " after ", iter, " iterations")
    else
        println("Failed to find root after ", max_iter, " iterations")
    end
    return x
end

# Initial guess
x0 = 1.0

# Tolerance and maximum number of iterations
tolerance = 1e-6
max_iterations = 1000

# Call the Newton-Raphson function
root = newton_raphson(f, df, x0, tolerance, max_iterations)

# Display the root
println("Root of the function is: ", root)
