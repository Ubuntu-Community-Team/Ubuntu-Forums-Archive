---
title: "Fortan to Python"
date: 2011-08-19
forum: General Help
---

### Post by anshulfy on 2011-08-19
Hi,

I have a big fortran code for FE analysis. I want to change the code to python. I am curious to know, whether I will get any advantage over speed, If not at least the speed shoud not be less than what fortran gives. Should I go for it. Please give your suggesions.

Thanks in advance.
--
Anshul

---

### Post by 3Miro on 2011-08-19
At best, Python will be marginally worse than Fortran. Probably, Python would be a lot worse.

Python has some use for Numerical Analysis, but only if it stands on top of C/C++ (or Fortran). It is useful to use Python to interface between different libraries, but making the code entirely in Python is a very bad idea.

If you want speed, you need something that compiles into native bytecode (C/C++, Fortran, Delphi .... ) If you want flexibility, you can put an interpretive language on top (Python, MATLAB, JavaScript).

---

### Post by anshulfy on 2011-08-19
Hey Miro,

Thanks for your reply.

---

