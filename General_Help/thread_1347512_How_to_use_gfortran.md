---
title: "How to use gfortran?"
date: 2009-12-06
forum: General Help
---

### Post by linux_dream on 2009-12-06
Hi,
It seems I've downloaded and installed gfortran.  However I don't know how to use it nor do I know where it is installed.  I'm very new to Ubuntu and if the program doesn't appear in the "Applications" list, it's probable I don't know where it is.
I've downloaded Emacs and I wrote a program in fortran 90, but how do I compile it?  How can I use gfortran?
I've been told to open the terminal and write 
gfortran test.f90 -o test

But even though there is the test.f90 file in my desktop, I received :
isaac@isaac-desktop:~$ gfortran test.f90 -o test
gfortran: test.f90: No existe el fichero ó directorio

If I translate from Spanish, it means that the file or directory doesn't exist...
Do you have any idea?

---

### Post by gordintoronto on 2009-12-06
Do you have a "programming" group?  If not, run Preferences/Main Menu and turn it on.  You might find Gfortran under Programming.

Did you install Gfortran through Synaptic, or download it from somewhere else?  Synaptic is the right way to go, that way it should appear in your Applications.

Once you can run Gfortran, you should be able to Open the program you have written.

---

### Post by linux_dream on 2009-12-06
> **gordintoronto said:**
> Do you have a "programming" group?  If not, run Preferences/Main Menu and turn it on.  You might find Gfortran under Programming.

Did you install Gfortran through Synaptic, or download it from somewhere else?  Synaptic is the right way to go, that way it should appear in your Applications.

Once you can run Gfortran, you should be able to Open the program you have written.
I've downloaded it from Synaptic (see my thread [http://ubuntuforums.org/showthread.php?t=1347574](http://ubuntuforums.org/showthread.php?t=1347574)).  Gfortran doesn't appear in the Programming list although I have this list in Applications.  In fact I'm not able to use any program I downloaded from Synaptic it seems...

---

### Post by sfp100 on 2010-05-25
> 
But even though there is the test.f90 file in my desktop, I received :
isaac@isaac-desktop:~$ gfortran test.f90 -o test
gfortran: test.f90: No existe el fichero ó directorio
Try ```
 cd Desktop
``` (mayby you need translate 'Desktop' to Spanish)
and then 
```
 gfortran test.f90 -o test 
```In console ```
 isaac@isaac-desktop:~$ 
```tilde ('~') means that you are in hour home directory (almost cases /home/user_name/, in your case: /home/isaac/ ), not in directory contains files from desktop (that is /home/username/Desktop/ in English language version, /home/username/Pulpit/ in Polish version, I don't know Spanish).

For future I suggest you to use separate folder for your Fortran codes: save all on desktop is horrible habit.

Good luck!

---

### Post by troykas on 2010-05-26
hey, i have also one problem :

i installed gfortran through package manager

than i did:

~/Documents$ gfortran hello.f
~/Documents$ gfortran a.out
a.out: file not recognized: File truncated
collect2: ld returned 1 exit status
~/Documents$ 

it seems that gfortran creates an executable a.out but it disappears when i try to run it.

after compilation i can see a.out as a file under documents
but after the command "gfortran a.out" it is deleted

can somebody help me please??

---

### Post by sfp100 on 2010-05-26
Hi, troykas
When you compile by 
```
gfortran file.f
```you get a.out -- executable file (program) that you can invoke by ```
 ./a.out 
```You don't need gfortran to run compiled program, only for compile the source to executable. If you omit './' system will search for a.out not in current directory, but in directories with binaries (/bin /usr/bin etc. full list you can obtain by 'echo $PATH').
Better way is to compile with
```
gfortran -o file file.f
```that produce executable file named 'file' -- you can run it by ```
./file
```CAUTION: if you write 'gfortran -o file.f file.f' you overwrite source file: name of compilation effect (executable) and source must differ, at least by extension.

Drop down is it understandable for you (I've got in my mind that my English is horrible).

Mayby you find usefull a textbook or tutorial for Fortran writen for Linux -- compiling and running programs differ a bit between Linux and Windows, and other operating systems (OS).

Good luck!

---

### Post by mazetas on 2010-09-18
I have the same problem. The matter is not that I can't compile. I can't even open the compiler. 
When I look for gfortran in programs menu, which I installed from synaptic and from konsole, it doesn't appear. When I try to open it from terminal it gives me 
```
gfortran: no input files 
```
and when I try to open from the folder /usr/bin it also doesn't do anything. Shouldn't a window compiler open somehow?

---

### Post by luigi_mb on 2010-09-19
gfortran is a CLI application, so open a terminal to use it.

```

man gfortran

```

/luigi

---

