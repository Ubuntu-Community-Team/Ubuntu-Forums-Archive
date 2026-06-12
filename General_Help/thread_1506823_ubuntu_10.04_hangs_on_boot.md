---
title: "ubuntu 10.04 hangs on boot"
date: 2010-06-10
forum: General Help
---

### Post by thunderpossum on 2010-06-10
Hiya, 

I installed 10 04 on my laptop because my Windows stopped working, I'm fine with that because I'm at least a bit familiar with the environment. 
Well, I had my install running how I like it but now when I turn it on it hangs in the splash screen.
I read on another forum that pressing shift when I turn the computer on along with a bunch of other stuff will help me boot, but when I press shift I just get a very quick error add it goes straight to the splash screen again.
Any help with this would be much appreciated.

Caleb

---

### Post by giddyup306 on 2010-06-10
> **thunderpossum said:**
> Hiya, 

I installed 10 04 on my laptop because my Windows stopped working, I'm fine with that because I'm at least a bit familiar with the environment. 
Well, I had my install running how I like it but now when I turn it on it hangs in the splash screen.
I read on another forum that pressing shift when I turn the computer on along with a bunch of other stuff will help me boot, but when I press shift I just get a very quick error add it goes straight to the splash screen again.
Any help with this would be much appreciated.

Caleb


Hello,

I'm still battling a similar problem.  I ran into this problem after doing an update.  Do you have an Nvidia or other proprietary video card?  

[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

---

### Post by thunderpossum on 2010-06-10
No. I'm afraid I don't have discreet graphics. I'm using an acer aspire one.

---

### Post by thunderpossum on 2010-06-10
I dunno how, but it fixed itself......

---

### Post by schloop on 2010-06-19
Hey, just had the same problem - a simple reboot from the shell seemed to resolve it.

(I'm still using Grub Legacy)

1) Hit 'Esc' to bring up the Grub menu when booting. Shift for Grub 2.0?
2) Select the 'Ubuntu 10.04 LTS, kernel 2.6.32-22generic **(recovery mode) **option.
3) Scroll down to the bottom of the Recovery Menu and select the 'root' option.
4) Enter 'shutdown -r now' into the shell.

:3

---

