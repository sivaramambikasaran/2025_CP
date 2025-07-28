# Numerical Integration

In contrast, adaptive techniques and the Romberg integration do not discard the previous function evaluations but use them to improve the solution accuracy when additional points are added.

## Exercises

1. **Relation between Padé scheme and Simpson’s rule**  
   What is the relation between the fourth-order central Padé scheme for differentiation and Simpson’s rule for integration? How can you use Simpson’s rule to derive the fourth-order Padé scheme?  
   *Hint: Start with*  
   $$
   \int_{x_{i-1}}^{x_{i+1}} f'(x) \, dx
   $$

2. **Discrete integration by parts**  
   Show that  
   $$
   \sum_{i=1}^{N-1} u_i \left.\frac{\delta v}{\delta x}\right|_i = - \sum_{i=1}^{N-1} v_i \left.\frac{\delta u}{\delta x}\right|_i + \text{boundary terms}
   $$  
   What are the boundary terms? Compare this discrete expression to the rule of integration by parts.

3. **Simpson’s rule accuracy**  
   Using the error analysis for the trapezoidal and rectangle rules, show that Simpson’s rule for integration over the entire interval is fourth-order accurate.

4. **Trapezoidal vs. Simpson’s rule**  
   Explain why in Example 3.1, the trapezoidal rule with end-correction is slightly more accurate than Simpson’s rule.

5. **Exact integration of polynomials**  
   Explain why the rectangle and trapezoidal rules can integrate a straight line exactly and the Simpson’s rule can integrate a cubic exactly.

6. **Fredholm integral equation**  
   A common problem of mathematical physics is that of solving the Fredholm integral equation  
   $$
   f(x) = \phi(x) + \int_a^b K(x,t)\phi(t) \, dt
   $$
   where the functions $ f(x) $ and $ K(x,t) $ are given and the problem is to obtain $ \phi(x) $.  
   (a) Describe a numerical method for solving this equation.  
   (b) Solve the following equation  
   $$
   \phi(x) = \pi x^2 + \int_0^\pi 3(0.5 \sin 3x - tx^2)\phi(t) \, dt
   $$
   Compare to the exact solution $ \phi(x) = \sin 3x $.

7. **Volterra integral equation**  
   Describe a method for solving the Volterra integral equation  
   $$
   f(x) = \phi(x) + \int_a^x K(x,t)\phi(t) \, dt
   $$  
   Note that the upper limit of the integral is $ x $. What is $ \phi(a) $?

8. **Singular integral**  
   $$
   \int_0^1 \left[ \frac{100}{\sqrt{x + 0.01}} + \frac{1}{(x - 0.3)^2 + 0.001} - \pi \right] dx
   $$  
   (a) Use the trapezoidal rule with $ n $ panels and plot log–log of error vs. $ n = 8, 16, 32, \ldots $  
   (b) Repeat using Simpson’s rule and trapezoidal rule with end-correction  
   (c) Evaluate using adaptive method (e.g. MATLAB `quad8`). Plot evaluation points.

9. **Refinement using two estimates**  
   Simpson’s rule was used for $ \int_0^1 f(x) dx $:  
   - $ h = 0.2 \rightarrow I = 12.045 $  
   - $ h = 0.1 \rightarrow I = 11.801 $  
   Use this info to get a more accurate value.

10. **Richardson extrapolation**  
    Compute $ f'(1.0) $ and $ f'(5.0) $ to 5-place accuracy using  
    $$
    f'(x) \approx \frac{f(x+h) - f(x-h)}{2h}, \quad f(x) = (x + 0.5)^{-2}, \quad h_0 = 0.5
    $$  
    Comment on convergence differences.

11. **Gauss quadrature**  
    Evaluate  
    $$
    I = \int_{-\infty}^{\infty} e^{-x^2} \cos(\alpha x) dx
    $$  
    for $ \alpha = 5 $. Exact solution: $ \sqrt{\pi}e^{-\alpha^2/4} $. Discuss evaluations required.

12. **Singularity handling**  
    Evaluate  
    $$
    I = \int_0^2 \frac{e^{-x}}{\sqrt{x}} dx
    $$  
    (a) Substitute $ x = t^2 $  
    (b) Use midpoint rule. Compare accuracy and cost.

13. **Truncation and transformation**  
    Evaluate  
    $$
    I = \int_0^{\infty} e^{-x^2} dx
    $$  
    (a) Truncate to [0, 4]  
    (b) Change variable $ t = 1/(1+x) $. Compare with exact: $ \sqrt{\pi}/2 $

14. **Adaptive trapezoidal rule**  
    Describe in detail an adaptive quadrature method using the trapezoidal rule. Show error estimate.

15. **Spline quadrature**  
    Evaluate  
    $$
    \int_0^\pi \sin(x) dx
    $$  
    (a) Use cubic spline interpolation  
    (b) Use 4, 8, 16, 32 intervals. Plot log–log error vs. points. Determine accuracy order.

16. **Compare integration strategies**  
    $$
    I = \int_{-\infty}^{\infty} e^{-x^2} \cos(2x) dx
    $$  
    (a) Gauss–Hermite quadrature with 8 nodes  
    (b) Map domain using $ \xi = \tanh(ax) $, find integrand at $ \xi = \pm 1 $  
    (c) Plot $ f(x) $ with 17 uniform $ \xi $ points for $ a = 2 $ and $ a = 0.4 $  
    (d) Use trapezoidal rule with 17 points and $ a = 0.4 $. Compare error with Simpson’s rule.

17. **Hybrid integration method**  
    Combine Simpson’s rule and trapezoidal rule with end correction to integrate  
    $$
    \int_{x_i-h}^{x_i+h} f(x) dx
    $$  
    using $ f(x_i \pm h), f(x_i), f'(x_i \pm h) $. What’s the order and global scheme?

18. **Romberg integration**  
    Even if coefficients $ c_i \neq c_i' $, $ \tilde{I}_{12} $ is fourth-order accurate.  
    (a) Show:  
    $$
    c_1 = -\frac{(b-a)}{12n} \sum_{i=0}^{n-1} f^{(2)}(y_i), \quad c_2 = -\frac{(b-a)}{480n} \sum_{i=0}^{n-1} f^{(4)}(y_i)
    $$  
    (b) Express $ c_i' $ using midpoints $ z_j $:  
    $ z_{2i} = y_i - h/4, \quad z_{2i+1} = y_i + h/4 $  
    (c) Show  
    $$
    c_1' = c_1 + \alpha_1 h^2 c_2 + \cdots
    $$  
    Determine $ \alpha_1 $ using Taylor expansion.

## Further Reading

- Abramowitz, M., and Stegun, I. *Handbook of Mathematical Functions with Formulas, Graphs, and Mathematical Tables*, Dover, 1972.  
- Dahlquist, G., and Björck, Å. *Numerical Methods*, Prentice-Hall, 1974, Chapter 7.  
- Ferziger, J. H. *Numerical Methods for Engineering Application*, 2nd ed., Wiley, 1998, Chapter 3.  
- Forsythe, G. E., Malcolm, M. A., and Moler, C. B. *Computer Methods for Mathematical Computations*, Prentice-Hall, 1977, Chapter 5.  
- Press, W. H., Teukolsky, S. A., Vetterling, W. T., and Flannery, B. P. *Numerical Recipes: The Art of Scientific Computing*, 3rd ed., Cambridge University Press, 2007, Chapter 4.