---
title: "Chrome Browser Launch Fail"
date: 2011-06-17
forum: General Help
---

### Post by zeke1312 on 2011-06-17
While attempting to use Chrome as my browser, the message"dependency not satisfied: libnspr 4.od (>=4.7.1)". Can you assist? Thank you

---

### Post by LordNeo on 2011-06-17
try to open a console an type:

sudo apt-get install libnspr4-0d

---

### Post by zeke1312 on 2011-06-17
Being new to this, how do I accomplish that? Thank you

---

### Post by wildmanne39 on 2011-06-18
> **zeke1312 said:**
> Being new to this, how do I accomplish that? Thank youHi, hit ctrl+alt+t when the terminal opens type
```
sudo apt-get install libnspr4-0d
```then you will have to enter your password that you setup when you created your user. It will not show the password being typed, then hopefully it will find the package and install it.

---

### Post by zeke1312 on 2011-06-18
Now I'll show you my real ignorance. What is "terminal opens"? How do I get there?

---

### Post by TheDoctorX on 2011-06-18
> **zeke1312 said:**
> Now I'll show you my real ignorance. What is "terminal opens"? How do I get there?

terminal is like the command prompt in win ... to open it open a new search clickin' on the top left button with the symbol of ubunto and write "terminal" then just type what he said before .. it's simple

---

### Post by zeke1312 on 2011-06-18
Clicking on the Ubuntu symbol gives me a drop down with various selections. I don't see a way to enter anything?

---

### Post by wildmanne39 on 2011-06-18
> **zeke1312 said:**
> Clicking on the Ubuntu symbol gives me a drop down with various selections. I don't see a way to enter anything?Hi, hold down the ctrl+alt+t key on the keyboard and that will open the terminal then follow my previous post, I am not sure that will install what you are missing but if it does not you can go from there and it should give a error message.

---

### Post by zeke1312 on 2011-06-18
Oops, I'm trying the ctrl/alt/7 keys and nothing happens? Geez I'm dumb. Sorry:( Any other suggestions?

---

### Post by wildmanne39 on 2011-06-18
> **zeke1312 said:**
> Oops, I'm trying the ctrl/alt/7 keys and nothing happens? Geez I'm dumb. Sorry:( Any other suggestions?Hi, yes read post #8 it is a t not a 7.

---

### Post by zeke1312 on 2011-06-18
Yes I tried that. Just typo on my post.

---

### Post by wildmanne39 on 2011-06-18
> **zeke1312 said:**
> Yes I tried that. Just typo on my post.
Hi, what happened did you get the terminal open? did you enter the command? did you enter you password as in my first set of instructions in post #4.

---

### Post by zeke1312 on 2011-06-19
See attachment. Using ctrl/alt/t gives me the attached screen.

---

### Post by wildmanne39 on 2011-06-19
> **zeke1312 said:**
> See attachment. Using ctrl/alt/t gives me the attached screen.Hi, you are running from a live cd, I do not think there is a reason to try to install anything like that, just use firefox, at least until you install ubuntu. When you install something with the livecd it will be gone when you restart your computer.

---

### Post by Cancelor on 2011-07-14
I have basically the same problem - Dependency is not satisfiable: libnspr4-0d (>= 4.7.1)

so  did the following, (I'm running from a pen drive):-

```
ubuntu@ubuntu:~$ sudo apt-get install libnspr4-0d
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libnspr4-0d is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libnspr4

E: Package 'libnspr4-0d' has no installation candidate
ubuntu@ubuntu:~$ sudo apt-get install libnspr4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libnspr4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ 
```but I still get the ' Dependency is not satisfiable: libnspr4-0d (>= 4.7.1)' message when I try to install Chrome.

Any sugestions?

---

### Post by o15977 on 2011-07-27
seeing your from live CD, you may have to update(update manager).... try that?

---

### Post by o15977 on 2011-07-27
> **wildmanne39 said:**
> Hi, you are running from a live cd, I do not think there is a reason to try to install anything like that, just use firefox, at least until you install ubuntu. When you install something with the livecd it will be gone when you restart your computer.

dude, i do the same! it's awesome to have a system portable wherever you go! (I don't think you can clone your disk, because the hardware driver at destination is prob different)
i use 64GB USB and put Ubuntu Live on, then remove Ubiquity, this way I can use it as my system, it's just as fast as booting from hard drive! I'm guessing the solution is to update!

btw whoever posted this, 
$cp -a  your /home to the /home at Flash drive!
you can also synchonise your /home whenever you go back onto your computer!(there's heaps programmes with interfaces) X)

---

