---
title: "Few simple questions"
date: 2009-09-16
forum: General Help
---

### Post by TheStroj on 2009-09-16
Hi everyone!

I don't like searching menus to find some stuff that i can access easier by using terminal, so I wonder if you can help me find some commands and solutions to my problems:

1. I want to see how much space is still available on the partitions where my Ubuntu is installed. Something like: Places - Computer - Filesystem - Properties. Any command to see this through terminal?

2. I'm using 64-bit Ubuntu 9.04 but every program says it is 32-bit. I was reading about this and people said that Ubuntu is using some 32-bit libraries. Any way to fix this? I can't use 64-bit programs.

3. When I turn on my computer, Ubuntu is using 5-6% of all my RAM (I have 4GB). But after some work, when i close all running programs it shows me 8+ %, but there is nothing running! 
If i use the "ps -aux" command i can't see any new programs opened. Are there any solutions for this, or do you think it's just a sensor bug?

4. If i play Extreme Tux Racer and i stop it, sometimes it still appears in process list ("ps -aux"). Even if I use the kill command on it, it doesn't stop but it keeps using my RAM and processor. Anyone knows how to stop it? (this has nothing to do with 3rd problem)

Please help as soon as possible, I really want to know this! ^^

Thank you!

---

### Post by TheStroj on 2009-09-16
These are simple questions so please help!

---

### Post by NightwishFan on 2009-09-16
If you are using 64-bit Ubuntu, you should already be using mainly AMD64 optimized programs. You just "can" use 32-bit libraries.

To check RAM use the command:
```
free -m
```
The line +/- buffers/cache is the most easy to understand.

If you kill a process you can check using the command 'top' or in the GNOME-System-Monitor if it is gone. Generally it should be.

---

### Post by TheStroj on 2009-09-16
> **NightwishFan said:**
> If you are using 64-bit Ubuntu, you should already be using mainly AMD64 optimized programs. You just "can" use 32-bit libraries.

To check RAM use the command:
```
free -m
```
The line +/- buffers/cache is the most easy to understand.

If you kill a process you can check using the command 'top' or in the GNOME-System-Monitor if it is gone. Generally it should be.
Well, I managed to kill that process and it works good now. 

Is there any 100% way to check if i have 32 or 64 bit Ubuntu? I borrowed the CD from my friend, hope he didn't screw up.

And the RAM thing is good now =).

---

### Post by NightwishFan on 2009-09-16
Use this command to check:
```
uname -a
```

---

### Post by TheStroj on 2009-09-16
> **NightwishFan said:**
> Use this command to check:
```
uname -a
```
I typed in the terminal:
uname -a
```
Linux...2.6.28-15-generic.....i686 GNU/Linux 
```
That's what it says...(without dots, I just made it shorter)
And uname-m writes:
```
i686
```
So i guess my friend gave me the wrong CD...
Thanks for your help anyway!

---

### Post by Wim Sturkenboom on 2009-09-16
Indeed 32 bit; for the diskspace, you can use *df -h*

---

