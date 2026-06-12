---
title: "installing j2ee - or how to make your life harder"
date: 2006-01-27
forum: General Help
---

### Post by nikosft on 2006-01-27
Dear everybody

I am using ubuntu 5.10 64bit . I am trying to install j2ee. when I try to execute the .bin file the following message appears: 

error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file:

I have installed libstdc++6 in my system. More over I try apt-file search libstdc++-libc6.2-2.so.3 and it returns nothing. I have already installed with success j2sdk 5

Can somebody give me a hint or tell me an alternative way to instal j2ee?

What is the point of making people life so difficult?

---

### Post by nikosft on 2006-01-28
Does ti have to do with the 64bit? Has anyone managed to install J2EE in 64bit machine?If so please send me a message.

---

### Post by Téragone on 2006-01-28
Where did you find a 64 bits version ? I don't see 64 bits version of J2EE.

---

### Post by nikosft on 2006-01-28
64bit version is my ubuntu not the j2ee

---

### Post by Téragone on 2006-01-28
Sure but 32 bits J2EE will need 32 bits library.

---

### Post by nikosft on 2006-01-28
A lot of people have the same problem in this forum but nobody seems to have the solution

So you tell me that these libraries missing are available only for the 32 bit version of Ubuntu?

Why the ubuntu people do not warn us before downloading the 64bit version "If you want to use this OS for your enterprise applications prefer Solaris or Windows XP instead" 

And do not tell me its a Sun's problem, because J2EE runs smoothly in WinXP 64bit. Even if somebody claim that it runs slower,its better that not running at all.

---

### Post by Téragone on 2006-01-29
I know that is possible to install the 32 bits library on a 64 Bits Ubuntu but I don't know how to do this. You will have to search this forum.

---

### Post by Jimmy_r on 2006-01-29
Try installing the packages starting with "lib32"

---

### Post by nikosft on 2006-01-29
I intalled 32bit Ubuntu and veryting works fine

---

