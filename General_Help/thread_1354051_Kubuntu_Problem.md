---
title: "Kubuntu Problem"
date: 2009-12-13
forum: General Help
---

### Post by warren181 on 2009-12-13
Hi

I got a new machine the other day and i decided to install Ubuntu and Kubuntu on the hard drive which is 40GB, I have the ubuntu partistion as 30GB and the kubuntu partition 10GB give or take a bit. I installed ubuntu first which works fine but when i installed kubuntu after it had asked me to restart and turned back on, the grub loader only had ubuntu options 2 which were the origonal install and update and the other was the kubuntu install. when i try to boot into the kubuntu OS it just goes to a black screen and wont do anything else, if someone could shead some light on this it would be great,.

Warren

---

### Post by Mr Nemo on 2009-12-13
Why install two separate operating systems? Install ubuntu or kubuntu and then install the other desktop enviroment. "sudo aptitude install kubuntu-desktop" in the terminal. Did that help?

---

### Post by lidex on 2009-12-13
Are these both karmic versions? If so you'll need to boot into whichever actually boots and update grub from there so it correctly detects the other. Grub2 is a change, but manageable none the less. Read about it here:
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by warren181 on 2009-12-14
Ill try the post above when i get home, but in a converstion i had with someone today i was wondering if my computer will handle KDE4, i only have a 2.4 celeron and 256MB RAM, and an intergrated graphics card.

Warren

---

### Post by lidex on 2009-12-14
You can test-drive kubuntu via LiveCD. Did you try it out first? The LiveCD is a beautiful thing.

---

### Post by warren181 on 2009-12-14
I did try that but that did not work but I thought that it might be because there is very little memory in the computer, and the ubuntu liveCD did not work but that intalled fine.

Warren

---

### Post by lidex on 2009-12-14
If overhead is a problem, maybe you should try xubuntu.
```
Minimum system requirements

You need 192 MB RAM to run the Live CD or 128 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM at install time.

To install Xubuntu, you need 2.0 GB of free space on your hard disk.

Once installed, Xubuntu can run with starting from 192 (or even just 128) MB RAM, but it is strongly recommended to have at least 256 MB RAM.

```

[http://www.xubuntu.org/get]("http://www.xubuntu.org/get")

A new PC shouldn't have problems with ubuntu or kubuntu aside from ram shortage but you can upgrade that.

---

### Post by warren181 on 2009-12-15
ok thanks for the help i will try wipping the hard drive and starting from scratch installing kubuntu first.

Warren

---

### Post by Grey Seal on 2009-12-16
I am currently running off my Freespire CD, cannot install it.

Earlier I downloaded Kubuntu 9.10 to a CDRW but my Optiplex gives me F1 or F2 options every time I choose install from CD. 

How can I get into my CD drive from the desktop in order to locate install...? Windows DOS base was so easy.

Regarding the partition, if you are not using the Kate files why split the drive? I have saved mine hoping to cut and paste onto Office.

---

