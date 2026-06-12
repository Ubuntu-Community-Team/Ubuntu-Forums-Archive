---
title: "Cant install Kubuntu 10.10"
date: 2010-11-25
forum: General Help
---

### Post by mastergunner on 2010-11-25
I have an issue with installing Kubuntu 10.10 on my computer. I put the cd and boot off of it. When I select start Kubuntu my screen goes blank and nothing reappears. I cannot install Kubuntu if I cant see what I need to select. Any help is appreciated. I have an AMD64 processor and am utilizing the appropriate Kubuntu version.

---

### Post by Rubi1200 on 2010-11-25
Hi,
what graphics card do you have installed?

---

### Post by mastergunner on 2010-11-25
I have an NVIDIA Geforce 8500.

---

### Post by Hippytaff on 2010-11-25
This might help, you need to select nomodset at boot and then go about installing the driver - here are a few ways to do the nomodset bit [http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

---

### Post by Rubi1200 on 2010-11-25
Put the LiveCD in and boot up;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameter:

nomodeset

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz nomodeset --**

Now hit Enter.

You may have to toggle the F6 option a bit (do it first etc.).

If this gets the LiveCD booted and to the desktop, then we can go from there for a more permanent solution.

---

### Post by Hippytaff on 2010-11-25
There you go ^^^^ lol

I'm so lazy sometimes :-)

---

### Post by mastergunner on 2010-11-25
The only thing I see is the screen that says Start Kubuntu. After that my screen goes blank so I cannot do anything after hitting Enter in your instructions.

> **Rubi1200 said:**
> Put the LiveCD in and boot up;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameter:

nomodeset

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz nomodeset --**

Now hit Enter.

You may have to toggle the F6 option a bit (do it first etc.).

If this gets the LiveCD booted and to the desktop, then we can go from there for a more permanent solution.

---

### Post by Rubi1200 on 2010-11-25
When you see Start Kubuntu, hit F6 instead and then try to go further with the instructions.

---

### Post by Hippytaff on 2010-11-25
> 
Important: hit F6 and then Esc to see the boot line

are you doing this bit? :-)

---

