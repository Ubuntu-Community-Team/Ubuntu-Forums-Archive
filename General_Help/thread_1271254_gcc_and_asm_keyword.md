---
title: "gcc and asm keyword"
date: 2009-09-20
forum: General Help
---

### Post by aloksethi on 2009-09-20
Hi,
I am not sure whether this post is valid for this forum or not, so please forgive me if i am wrong

i am trying to write a c code using asm extention


```

int fun(int in)
{
 int b=2;
asm("movl $100, %0;"
    "test %1, %1;"
    "cmovl %1, %0;"
    : "=r" (b)
    : "r" (in)
    );
return b;
}

int main()
{
int a=8;
int b;

b = fun(-1);
printf("%d %d\n",a,b);
}

```

the output of above code should be "8 -1", ie the value of "b" in main after calling "fun" should be "-1". instead the output is "8 100"


the assemble output is
```

fun:
  pushl %ebp
  movl  %esp, %ebp
  subl  $16, %esp
  movl  $2, -4(%ebp)
  movl  8(%ebp), %eax
#APP
# 6 "asm.c" 1
  movl $100, %eax;test %eax, %eax;cmovl %eax, %eax;
# 0 "" 2
#NO_APP
  movl  %eax, -4(%ebp)
  movl  -4(%ebp), %eax
  leave
  ret
```


from the assembly output u can see that, gcc is using eax to store variable "in", and it is also using eax at place where it should be using any register for variable "b"

i am not sure that whether its a bug or something i am doing wrong
I am using gcc 4.3.2

sethi@sethi-laptop:~/code$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.2-1ubuntu11' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11)


please help
thanks
alok

---

### Post by ibuclaw on 2009-09-21
> **aloksethi said:**
> Hi,
I am not sure whether this post is valid for this forum or not, so please forgive me if i am wrong

i am trying to write a c code using asm extention


I don't know why you are moving $100 to %0, but removing that line fixes the issue.

```

int fun(int in)
{
    int b=2;
    asm("test %1, %1;"
        "cmovl %1, %0;"
        : "=r" (b)
        : "r" (in)
       );
    return b;
}

int main()
{
    int a=8;
    int b;

    b = fun(-1);
    printf("%d %d\n",a,b);
}

```

Regards
Iain

---

### Post by aloksethi on 2009-09-22
actually it doesn't solve the issue.
my main motto of  writing this code was to test the "cvmol" instruction.
so basically whenever the test instruction will show that the result is less than 0, the "cmov" instruction should move the data

i used the mov instruction so that initially 100 gets moved into variable "b" and if the test ins indicate the input value is -ve, cmov instruction should move the input value to the variable "b"


int fun(int in)
{
        int b=2;
        asm("mov $100, %%ebx;"
            "test %1, %1;"
            "cmovl %1, %%ebx;"
            "mov %%ebx, %%eax;"
            "leave;"
            "ret;"
           : "=r" (b)
           : "r" (in)
           );
        return b;
}


so if u call fun with +ve argument, it will always return 100, if called with -ve argument it will return the -ve value

just check the assembly code that gcc is generating for the original code i posted, u will see that gcc is using eax for both %0 and %1, why gcc is doing this that is a mystery for me

---

### Post by aloksethi on 2009-09-22
problem solved
have to specify variable "b" as earlyclobber operand

[http://gcc.gnu.org/onlinedocs/gcc-4.2.4/gcc/Modifiers.html#Modifiers](http://gcc.gnu.org/onlinedocs/gcc-4.2.4/gcc/Modifiers.html#Modifiers)

```
 asm("mov $100, %0;"
            "test %1, %1;"
            "cmovl %1, %0;"
           : "=&r" (b)
           : "r" (in)
           );
```

thanks

---

### Post by ibuclaw on 2009-09-22
> **aloksethi said:**
> problem solved
have to specify variable "b" as earlyclobber operand

[http://gcc.gnu.org/onlinedocs/gcc-4.2.4/gcc/Modifiers.html#Modifiers](http://gcc.gnu.org/onlinedocs/gcc-4.2.4/gcc/Modifiers.html#Modifiers)

```
 asm("mov $100, %0;"
            "test %1, %1;"
            "cmovl %1, %0;"
           : "=&r" (b)
           : "r" (in)
           );
```

thanks

Oh I see now.

Haven't used the asm() function in gcc much, but glad you worked it out.

Regards
Iain

---

