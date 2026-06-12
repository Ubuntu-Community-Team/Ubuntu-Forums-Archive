---
title: "how to install CMake?????? please help!"
date: 2009-09-10
forum: General Help
---

### Post by liquidmonkey on 2009-09-10
ok, just installed ubuntu and did all the updates for 9.04.
i want to install a program called player / stage but before i do that i need something called CMake which is here....

[http://www.cmake.org/cmake/resources/software.html](http://www.cmake.org/cmake/resources/software.html)

there are two packages listed ending in tar.gz and tar.Z respectively.

can someone explain to me (like i'm a 2 year old monkey) how to get that file and then what to do with it?

at the moment i'm looking at the UBUNTUpocketGUIDE which is great but fails to address my above question.

i know this is basic basic but i'm just not getting it :(

---

### Post by mefiiik on 2009-09-10
> **liquidmonkey said:**
> ok, just installed ubuntu and did all the updates for 9.04.
i want to install a program called player / stage but before i do that i need something called CMake which is here....

[http://www.cmake.org/cmake/resources/software.html](http://www.cmake.org/cmake/resources/software.html)

there are two packages listed ending in tar.gz and tar.Z respectively.

can someone explain to me (like i'm a 2 year old monkey) how to get that file and then what to do with it?

at the moment i'm looking at the UBUNTUpocketGUIDE which is great but fails to address my above question.

i know this is basic basic but i'm just not getting it :(

you have to extract thath zip file *.tar.gz... open it in console(terminal).. and write ```
./configure
```
wait until it end and write
```
make
```
again wait and at least write 
```
make install
```

if you will have some troubles you have to install gtk
```
sudo apt-get install libgtk2.0-dev
```

and again do ./configure...make.make install

hope it help:)

---

### Post by PriceChild on 2009-09-10
On Linux, installing random software off of random internet sites is bad... and as a user you want to compile as little as possible.

CMake **is** in the repositories, so please don't attempt installation using the above post.

Could you give us a link to the website of the actual software you want to install? Hopefully we'll be able to find an easy way to do it.

---

### Post by liquidmonkey on 2009-09-10
here is the main program(s) that i want to install.

[http://playerstage.sourceforge.net/](http://playerstage.sourceforge.net/)

i need version 2.11 as apparently the newest ones give problems (according to my prof).

if CMake is in the reposiwhatever then how to do i install that?


THANKS FOR THE FAST RESPONSE...NICE!

---

### Post by liquidmonkey on 2009-09-10
> **mefiiik said:**
> you have to extract thath zip file *.tar.gz... open it in console(terminal).. and write ```
./configure
```


c, u already lost me. how do i OPEN the .tar.gz in the terminal?
and whats the difference between the .tar.gz and the .tar.Z? are they both same? do i need them both? are they just different compressed versions of the one file?

---

### Post by mefiiik on 2009-09-10
> **liquidmonkey said:**
> c, u already lost me. how do i OPEN the .tar.gz in the terminal?
and whats the difference between the .tar.gz and the .tar.Z? are they both same? do i need them both? are they just different compressed versions of the one file?
i am beginner but i have same problem... just open the tar.gz and extract it to the desktop... then open terminal and write
```
cd Desktop
```
then
```
cd xxxx
``` where xxxx is folder where is extracted the tar.gz
and when you will have in terminal 
```
~/Desktop/xxxx$
```
write ```
./configure
```... and make.. and make intsall

---

### Post by liquidmonkey on 2009-09-10
> **mefiiik said:**
> i am beginner but i have same problem... just open the tar.gz and extract it to the desktop... then open terminal and write
```
cd Desktop
```then
```
cd xxxx
``` where xxxx is folder where is extracted the tar.gz
and when you will have in terminal 
```
~/Desktop/xxxx$
```write ```
./configure
```... and make.. and make intsall

THANKS!
ok, cool. made it down to the 'make' part but i get an error telling me i don't have the right c++ compiler on my system :(


now what? man, i thought this was gonna take 30minutes max. have been getting ubuntu ready for 3 hours :(

ok, c++ compiler, where do i get that?

---

### Post by mefiiik on 2009-09-10
> **liquidmonkey said:**
> THANKS!
ok, cool. made it down to the 'make' part but i get an error telling me i don't have the right c++ compiler on my system :(


now what? man, i thought this was gonna take 30minutes max. have been getting ubuntu ready for 3 hours :(

ok, c++ compiler, where do i get that?
  try```
sudo aptitude install build-essential

```
this may help

---

### Post by liquidmonkey on 2009-09-10
> **mefiiik said:**
> try```
sudo aptitude install build-essential

```this may help


yup, it did something :) haha!
tried the 'make' and 'make install' again but no luck :( or is CMake installed now?

---

### Post by mefiiik on 2009-09-10
> **liquidmonkey said:**
> yup, it did something :) haha!
tried the 'make' and 'make install' again but no luck :( or is CMake installed now? did you do this step 
sudo apt-get install libgtk2.0-dev ???

---

### Post by liquidmonkey on 2009-09-10
just did that, thanks!

and then i did

./ configure
make
make install (got an error on that one though :(

is that right? am i done?

---

### Post by mefiiik on 2009-09-10
> **liquidmonkey said:**
> just did that, thanks!

and then i did

./ configure
make
make install (got an error on that one though :(

is that right? am i done?
maybe:D i told you i am beginner... look in to "media" or how it is called "video/music" something like this.. you have to see here CMake player...

---

### Post by liquidmonkey on 2009-09-10
> **mefiiik said:**
> maybe:D i told you i am beginner... look in to "media" or how it is called "video/music" something like this.. you have to see here CMake player...


haha, no worries.
CMake as far as i know is NOT a player of sorts but it allows me to use c++ programs and so on. either way i need it for PLAYER / STAGE.


does any1 know how i can check if the CMake install worked?

---

### Post by mefiiik on 2009-09-10
> **liquidmonkey said:**
> haha, no worries.
CMake as far as i know is NOT a player of sorts but it allows me to use c++ programs and so on. either way i need it for PLAYER / STAGE.


does any1 know how i can check if the CMake install worked?oh sorry:D try this
[http://www.vtk.org/Wiki/CMake_Testing_With_CTest](http://www.vtk.org/Wiki/CMake_Testing_With_CTest)

---

### Post by liquidmonkey on 2009-09-10
[http://www.vtk.org/Wiki/CMake_FAQ#What_is_CMake.3F](http://www.vtk.org/Wiki/CMake_FAQ#What_is_CMake.3F)

still don't know if its installed though :(

---

### Post by liquidmonkey on 2009-09-10
does CMake come up in the 'add/remove applications' window?

---

