---
title: "How do I install and setup Burg?"
date: 2010-12-29
forum: General Help
---

### Post by BKbroila on 2010-12-29
I've got Win7 and 10.10 running, and I've tried installing Burg, but my very-basic knowledge of Ubuntu and GRUB has got me confused. I've tried looking up how to get this working, but couldn't find anything online. Fortunately, I installed Windows first, so there shouldn't be a problem there.

I read about Burg first over at Lifehacker and a comment said to enter in these lines in terminal, which I did: 
sudo add-apt-repository ppa:bean123ch/burg  
sudo apt-get update  
sudo apt-get install burg

I've run this twice, but from what I remember, I think a popup came up, with nothing too special (I'm running Windows right now, sorry)


But what do I do now?
How do I 'access' Burg or modify it?

Like I said, my knowledge is very basic, so I'd like instructions in the very-basic format.

Thanks

---

### Post by dcstar on 2010-12-29
> **BKbroila said:**
> I've got Win7 and 10.10 running, and I've tried installing Burg, but my very-basic knowledge of Ubuntu and GRUB has got me confused. I've tried looking up how to get this working, but couldn't find anything online. Fortunately, I installed Windows first, so there shouldn't be a problem there.

I read about Burg first over at Lifehacker and a comment said to enter in these lines in terminal, which I did: 
sudo add-apt-repository ppa:bean123ch/burg  
sudo apt-get update  
sudo apt-get install burg

I've run this twice, but from what I remember, I think a popup came up, with nothing too special (I'm running Windows right now, sorry)


But what do I do now?
How do I 'access' Burg or modify it?

Like I said, my knowledge is very basic, so I'd like instructions in the very-basic format.

Thanks

```
sudo dpkg-reconfigure burg-pc
```
[https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)

---

### Post by Quadunit404 on 2010-12-29
I see you've already got the PPA. You want to run the command
```
sudo apt-get install burg-pc burg-themes burg-emu burg-common burg-themes-common
```
That'll give you burg.

When it asks you where you want to install burg, say /dev/sda (if that's your internal drive.) When it asks you to set the Linux default command line, set it to [FONT="Courier New"]quiet splash[/FONT].

I followed [this]("http://www.open-tutorial.com/2010/07/27/install-burg-to-replace-grub-in-ubuntu/") guide and Burg works perfectly. Required some hax to get it to display at my monitor's resolution of 1366x768 but hey, I can boot Ubuntu and Windows.

Also, you may want to look at [Grub Customizer.]("http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html") It supports Burg as of version 1.1 and will let you configure Burg instead of Grub if it finds a working Burg installation.

PS: Remember to use burg-update when you update your kernel or install another OS!

---

### Post by BKbroila on 2010-12-31
I was about to say thanks, when I ran into a problem.
I missed the part entering blank  for Linux command Line, and so I messed up...
I tried getting the autoinstaller and reinstalling, but that didn't work. Is there a way to start from the beginning?? I tried getting the burg.cfg file, but that comes up as blank.... so I'd like to restart this process by uninstalling everything first.

---

### Post by dcstar on 2010-12-31
> **BKbroila said:**
> I was about to say thanks, when I ran into a problem.
I missed the part entering blank  for Linux command Line, and so I messed up...
I tried getting the autoinstaller and reinstalling, but that didn't work. Is there a way to start from the beginning?? I tried getting the burg.cfg file, but that comes up as blank.... so I'd like to restart this process by uninstalling everything first.

```
sudo dpkg-reconfigure burg-pc
```

---

### Post by BKbroila on 2011-01-01
Still getting the GRUB screen.... 
This is making me sad...

---

### Post by dcstar on 2011-01-01
> **BKbroila said:**
> Still getting the GRUB screen.... 
This is making me sad...

If you are getting the Grub screen then you have **not** installed the Burg bootloader on the MBR of the drive your BIOS is booting from.

Where did you install it?

---

### Post by BKbroila on 2011-01-02
Well, after pressing every possible key on the install location screen, I figured it out!
A simple * to the location input was it...
Thanks though for helping out

---

