---
title: "No Display"
date: 2011-03-01
forum: General Help
---

### Post by jaredmanning on 2011-03-01
I just installed Ubuntu 10.10 on my PC.  When I start the computer, GRUB pops up and I select the top Ubuntu one, but then I don't see any display.  I hear the sounds of the login screen, I can login in and continue, but I still don't see anything on the screen, and my monitor goes to sleep.

some specs:
intel Core 2 Duo
1 TB Hard Drive (Windows 7)
500 GB Hard Drive (Ubuntu 10.10)
nvidia GeForce 8400 graphics card

---

### Post by Animal X on 2011-03-01
...while we're waiting on answers, have you tried a different kernel or a live cd to compare?

---

### Post by jaredmanning on 2011-03-01
I have tried the 32-bit and 64-bit of 10.10, I just did this today, and I have to work on other stuff in the meantime

---

### Post by jerome1232 on 2011-03-01
What kind of monitor is this, CRT or LCD? Did it work at all before? Have you installed the Nvidia proprietary driver?

just from the info provided it sounds to me like Ubuntu is choosing a resolution/refresh rate that is out of your monitors range.

---

### Post by Animal X on 2011-03-01
my experience is limited, but what im getting at is, you said you picked the 'top' one, was there a second or third entry you could try? have you? and the 32 or 64 bit thing, are you staying you did installations? or were they live cd's? is this something that hasnt worked from the get-go, or did it just start acting up?

---

### Post by jaredmanning on 2011-03-01
LCD.  I have the prop driver for the card, and it works for everything else.  how do I get it to switch? is it possible i can do it in the console? because i can just open that blindly and type

---

### Post by jerome1232 on 2011-03-01
Can you get a tty that works by pressing ctrl+alt+F1?

If you can get into that tty then log in and try running nvidia-xconfig, 

Looking at then man page for nvidia-xconfig you can specify a list of modes.

So maybe something like this (if your lcd ran at a native 1024x768 resolution)

sudo nvidia-xconfig --mode-list=1024x768

---

### Post by jaredmanning on 2011-03-02
Thank you, I will try that right now!

---

