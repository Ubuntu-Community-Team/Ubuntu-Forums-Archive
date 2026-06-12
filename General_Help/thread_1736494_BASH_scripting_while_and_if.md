---
title: "BASH scripting while and if?"
date: 2011-04-22
forum: General Help
---

### Post by javajames97 on 2011-04-22
I enjoy programming, but im not the kind of person that want's to work on GUI. I'm quite young and just want to use a simple program for compiling my programs, similar to python IDLE, but for java and C++. So i use the GCC, which includes gcc (c), g++ (c++), gcj (java) ect. And i simply compile my programs in BASH, it is good because it has only 2 features; a compiler and a feedback system that reports bugs. It means i have to manually debug my programs, but i don't write massive scripts anyway, just little programs for experiment. So i began learning how to script in BASH in order to create a BASH script that does all the different stuff i would usually do to compile my programs by itself. It asks you whether you want to compile in c++ or java, it asks you for file names (fname = filename : cname = compiled filename), then it opens gedit with your file, when you exit gedit, it compiles and runs my program, then goes back and does it again (from gedit) here is the code:
```

#!/bin/bash
echo 'welcome to the simple compiler, you can exit at any time with keyboard interupt (ctrl C) or by closing the program.'
echo "Enter 'c' for C/C++ compiler or 'j' for java compiler:"
read typ
ver=1
echo 'enter filename:'
read fname
echo 'enter compiled name:'
read cname
echo 'program will begin'
if [ typ = 'c' ]; then
   while [ $ver = 1 ]; do
       gedit Ccoding/$fname
       echo 'compile and program results'
       g++ Ccoding/$fname -o Ccoding/Compiled/$cname
       if [ -a Ccoding/Compiled/$cname ]; then
           ./Ccoding/Compiled/$cname
       fi
       sleep 2
elif [ typ = 'j' ]; then
   while [ $ver = 1 ]; do
       gedit Jcoding/$fname
       echo 'compile and program results'
       gcj Jcoding/$fname -o Jcoding/Compiled/$cname
       if [ -a Jcoding/Compiled/$cname ]; then
           ./Jcoding/Compiled/$cname
       fi
       sleep 2
fi

```

my problem is that when i run this, it makes it through the first bit, but then it fails at the if and while statements, but i don't know which ones are wrong, and how they are wrong, could somebody show me the proper use of while and if loops in BASH scripting?

---

### Post by Vaphell on 2011-04-22
while has to be closed with 'done' (for loop too)

---

### Post by javajames97 on 2011-04-22
> **Vaphell said:**
> while has to be closed with 'done' (for loop too)

tried putting done in line with while and in line with the contents of while, something else is wrong

---

### Post by doas777 on 2011-04-22
in the if statement conditions, when comparing numerics, try using '-eq' instead of '='

[ $ver -eq 1 ]

---

### Post by Vaphell on 2011-04-22
missing $ in if condition ($typ)

---

### Post by javajames97 on 2011-04-22
```

#!/bin/bash
echo 'welcome to the simple compiler, you can exit at any time with keyboard interupt (ctrl C) or by closing the program.'
echo "Enter 'c' for C/C++ compiler or 'j' for java compiler:"
read typ
ver=1
echo 'enter filename:'
read fname
echo 'enter compiled name:'
read cname
echo 'program will begin'
if [ $typ -eq 'c' ]; then
   while [ $ver -eq 1 ]; do
       gedit Ccoding/$fname
       echo 'compile and program results'
       g++ Ccoding/$fname -o Ccoding/Compiled/$cname
       if [ -a Ccoding/Compiled/$cname ]; then
           ./Ccoding/Compiled/$cname
       fi
       sleep 2
   done

elif [ $typ -eq 'j' ]; then
   while [ $ver -eq 1 ]; do
       gedit Jcoding/$fname
       echo 'compile and program results'
       gcj Jcoding/$fname -o Jcoding/Compiled/$cname
       if [ -a Jcoding/Compiled/$cname ]; then
           ./Jcoding/Compiled/$cname
       fi
       sleep 2
   done
fi
sleep 20

```

so i have added a sleep on the end, and this is what i got:
```

welcome to the simple compiler, you can exit at any time with keyboard interupt (ctrl C) or by closing the program.
Enter 'c' for C/C++ compiler or 'j' for java compiler:
c
enter filename:
sim_arith.c
enter compiled name:
arith
program will begin
/home/james/Desktop/coding/sim_comp: line 11: [: c: integer expression expected
/home/james/Desktop/coding/sim_comp: line 22: [: c: integer expression expected

```

so it is my if statements, but integer expression?

---

### Post by doas777 on 2011-04-22
yes. note my post about using -eq with ***Numeric*** types. 'j' is not a numeric type. use an = sign in that case. sorry, I should have made that clearer.

---

### Post by Vaphell on 2011-04-22
you can upgrade your script to guess from file extension which compiler to use
```
ext=${fname##*.}
echo extension $ext
case $ext in
  c    ) typ='c' ;;
  c++  ) typ='c' ;;
  java ) typ='j' ;;
  *    ) echo unknown type ;;
esac
```

also seeing how both blocks are nearly identical you can modify your script to use only 1
for example
```
case $ext in
    c    ) typ='C'; compiler=gcc ;;
    c++  ) typ='C'; compiler=g++ ;;
    java ) typ='J'; compiler=gcj ;;
esac

while [ $ver -eq 1 ]; do
    gedit **${typ}**coding/$fname
    echo 'compile and program results'
    **${compiler}** **${typ}**coding/$fname -o **${typ}**coding/Compiled/$cname
    if [ -a **${typ}**coding/Compiled/$cname ]; then
        ./**${typ}**coding/Compiled/$cname
    fi
    sleep 2
done

```

---

