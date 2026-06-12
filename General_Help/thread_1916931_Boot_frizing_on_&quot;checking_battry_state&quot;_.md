---
title: "Boot frizing on &quot;checking battry state&quot; ubuntu 11.10"
date: 2012-01-29
forum: General Help
---

### Post by CProgramming on 2012-01-29
Hello all
I have problem with ubuntu 11.10 
I have installed ubuntu 11.10 and its worked well , first boot.
Ubuntu ask for install nVidia-173 drivers and update , I'v installed and since the next boot , I can't use Ubuntu. 
Can someone help me?
By the way , when I'm booting , Ubuntu loading screen I huge , because booting resulution is 800x600 , but my screen is 1680x1050.
How can I fix it?

My grphics card is **nvidia GeForce 430**.

Thanks !

---

### Post by 2F4U on 2012-01-29
From your post I assume that it worked with the initial open source drivers that came with Ubuntu? Is there any particulara reason for not using those drivers?

---

### Post by CProgramming on 2012-01-29
> **2F4U said:**
> From your post I assume that it worked with the initial open source drivers that came with Ubuntu? Is there any particulara reason for not using those drivers?

mm .. When I boot first timeubuntu ask for update drivers. since I update , I have this boot problem ..

---

### Post by forza.stiinta on 2012-02-16
I have this problem too.

Each time there is a kernel update, the system halts at "checking battery status". The solution is booting into command line and reinstall nvidia drivers. I use the latest drivers from nvidia.

it is annoying to do this after each kernel update, but i did not find any solutions...

---

### Post by NikoC on 2012-02-16
I 've been having the same problem for months now on Kubuntu 11.04 64bit.

Tried a couple of solution such as:
- sudo apt-get install kubuntu-desktop
- reinstall nvidia-173

But to no avail! I have my kernel 3.0.14 locked in package management because newer kernels do not let me resume from suspend and still the issue persists!

---

