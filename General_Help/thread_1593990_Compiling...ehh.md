---
title: "Compiling...ehh?"
date: 2010-10-11
forum: General Help
---

### Post by cancer10 on 2010-10-11
Hi

I have read on random sites where people say, "GD library needs to be compiled with PHP".

I want to know two things:

1) What does compiling mean?
2) How does one compile GD with PHP?



Thanks

---

### Post by Barriehie on 2010-10-11
> **cancer10 said:**
> Hi

I have read on random sites where people say, "GD library needs to be compiled with PHP".

I want to know two things:

1) What does compiling mean?
2) How does one compile GD with PHP?



Thanks

Compiling is the process of taking the source code, human readable, and passing it to a 'compiler' that makes the machine code the computer needs to run the program.  PHP is an interpreted language so I can't really help you in regards to 'compiling' it.

HTH

---

### Post by lisati on 2010-10-11
After briefly scanning [this page]("http://www.boutell.com/gd/faq.html"), I suspect that they are referring to using GD *with* PHP

---

### Post by cancer10 on 2010-10-11
> **lisati said:**
> After briefly scanning [this page]("http://www.boutell.com/gd/faq.html"), I suspect that they are referring to using GD *with* PHP

You mean, if I run this code in the terminal, it means I am compiling GD with php?


```
up2date php-gd 
```

---

### Post by lisati on 2010-10-11
The "up2date php-gd" command you cite is for Red-Hat Linux. In Ubuntu, you'd use something like:
```
sudo apt-get install php-gd
```

---

### Post by cancer10 on 2010-10-11
> **lisati said:**
> The "up2date php-gd" command you cite is for Red-Hat Linux. In Ubuntu, you'd use something like:
```
sudo apt-get install php-gd
```

So more or less this is how you compile GD with PHP?

---

### Post by lisati on 2010-10-11
> **cancer10 said:**
> So more or less this is how you compile GD with PHP?

No. It installs php-gd, which is one of the tools you might need to **use** GD with PHP.

---

### Post by cancer10 on 2010-10-11
okay but then whats the command to compile?

---

### Post by lisati on 2010-10-11
One does not ordinarily compile with PHP. It is a scripting language commonly used to present web pages from a server. 

What were you trying to do when you got the original error message?

---

### Post by cancer10 on 2010-10-11
I was not trying to do anything. I asked because I wanted to know how can one do compiling.

---

### Post by lisati on 2010-10-11
Have a look [here]("http://en.wikipedia.org/wiki/Compiler") and [here]("http://ubuntuforums.org/forumdisplay.php?f=39")

---

### Post by Ahava591 on 2010-10-12
> **cancer10 said:**
> I was not trying to do anything. I asked because I wanted to know how can one do compiling.
Compiling would be in the programming section; not general help. However, this is installing a package.

Very broadly speaking, PHP is not a compiled language. Once you write the code it is passed to the interpreter to run; commonly found with "scripting," languages such as Python and Perl. The source code, which is what you write, is passed to the interpreter which translates your source code into what's usually called "bytecode," which can then be run by the computer as a program. This is a very general description.

-Think of the Python interpreter. You could theoretically code "interactively," with the interpreter because your code that you type in is passed to the interpreter as you need to run it. 

This is in contrast to a compiled language like C. With a compiled language, you write the source code and this is then run through a compiler to be translated into binary; I think the main use of compilers is to create a binary executable.

An example would be the Linux kernel, (which is where the "Linux," in Linux comes from.) The kernel is written I think in C; if not entirely the kernel is at least mostly C code. The kernel must be compiled for it to do anything. Some distributions require you to compile all of the source code yourself for the operating system as well as applications that you wish to use when you install the distro.
-In such a case, you will generally download the source code files for all of the aforementioned software; then you use a compiler to compile each source. You could think of it as "building," the distro yourself.


I recommend you head over to the programming section for more, and better, information than I can offer you.

Good luck.

---

