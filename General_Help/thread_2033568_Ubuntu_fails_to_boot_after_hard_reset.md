---
title: "Ubuntu fails to boot after hard reset"
date: 2012-07-26
forum: General Help
---

### Post by cyanide911 on 2012-07-26
Basically I had to hard shutdown (from the power button) my computer while Ubuntu (12.04 64bit) was running. 

Now when I boot my computer, instead of the purple GRUB background, I'm seeing a Debian background with a part of the earth showing along with a few stars. If I boot into Ubuntu, after some scrolling text it gets stuck on a black screen. Nothing happens. No cursor even.

How do I solve this? I tried to boot into the Ubuntu live CD and 'Check' my EXT4 partition, but that did not solve anything.



***EDIT: I've written reset instead of shutdown in the title, sorry.***

---

### Post by Jay MC on 2012-07-26
Although I normally can hard power-off just fine, I'm afraid I also had this problem once with a different laptop.  I didn't solve it (I was only going to be using the machine for a few weeks so made do with Windows for the remainder of the time).  Not the answer you're looking for  :(  but hopefully someone else has a fix for you.

I'm chipping it because, in addition to you needing a fix for your own computer, I would like to ask if anyone knows why this happens and if it's avoidable (e.g., "it's safe to hard power-down if X but not if Y").  I would hate to scupper my main Ubuntu install.

---

### Post by Dylan1473 on 2012-07-26
If you boot into the liveCD and look at the partition with Ubuntu on it are there still files there? If worst comes to worst you can at least recover anything important and reinstall. It would also speak a lot better of your chances at recovering your install.

EDIT: I'd add that I also have that debian splash screen, I'm not sure why. It's been like that since I briefly tried Debian, it didn't go away when I reinstalled Ubuntu. I guess it just kept the old bootloader and changed the entries.

---

### Post by cyanide911 on 2012-07-26
Data recovery isn't really a concern, I had nearly nothing in that partition. Why I don't want to reinstall it is because I'd have to go through the long process of setting up my AMD/Intel hybrid graphics again.

There has to be a solution, I don't think anything that major could've happened. But then again, I know very little about all this.

---

### Post by cyanide911 on 2012-07-26
Oookay now it seems to be getting worse. It's getting stuck at different stages. This time, it's stuck at 

> * Stopping LightDM Display Manager

in the previous boot it was stuck at a different seemingly random step.

F1, CTRL F1, CTRL ALT F1 etc don't work :(


EDIT: Whoa, I added radeon.modeset=0 in GRUB to Ubuntu and it's booted up fine! 

What does this mean though? Are my drivers broken, or will I find something not working?

---

