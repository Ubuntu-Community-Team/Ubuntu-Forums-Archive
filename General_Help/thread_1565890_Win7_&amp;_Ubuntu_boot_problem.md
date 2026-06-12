---
title: "Win7 &amp; Ubuntu boot problem"
date: 2010-09-01
forum: General Help
---

### Post by phantom27 on 2010-09-01
I had Win7 installed on my laptop. I used the Ubuntu windows installer to install ubuntu (which I now like more than windows).
 
When I boot my laptop I get a windows boot loader that gives me the option of booting Windows 7 or Ubuntu (if I don't do anything for awhile it auto loads Win7). If I choose ubuntu "sometimes" I get another bootloader giveing me the option of multiple installs of Ubuntu (it looks like the orginial install + safemode and a newer version +safemode and windows 7 also). I choose the newest version of ubuntu and it runs fine. 
 
At first this was fine because I liked Win 7 more. Now I am totally converted to Ubunutu (I'm on the verge of formating the entire thing and installing ubuntu fresh). Now I want the comptuer to boot into a bootloader that will automaticly choose ubuntu in a couple of seconds (or even automaticly choose ubuntu unless I hit a key or something). 
 
Any ideas how to fix this? Oh... I'm a nerd but a total Ubuntu (and linux) newbe.

---

### Post by Mark Phelps on 2010-09-01
Install startup-manager from Synaptic and, once installed, run it and select Ubuntu as the default.  

After that, it will boot into Ubuntu without you having to select it manually.

---

### Post by wilee-nilee on 2010-09-01
This is a wubi install I believe.

---

### Post by phantom27 on 2010-09-01
> **wilee-nilee said:**
> This is a wubi install I believe.
 
Yes it is.  I just couldn't remember the name of the install.  Does that mean that startup-manager won't work?

---

### Post by wilee-nilee on 2010-09-01
> **phantom27 said:**
> Yes it is.  I just couldn't remember the name of the install.  Does that mean that startup-manager won't work?

Startup manager wont work.

If you dual boot the computer you could use this program to default the OS. If you want to dual boot give us a screenshot/snip of the disk manager in windows. 

Personally I would hold on to the windows setup or at least have a way to reinstall, so what do you have, and what do you want in this area? I'm a 99.99% open source user but if I have a license I keep it usable.

Windows 7 can be shrunk down pretty small if done correctly, giving more space to a real dual booted Ubuntu.

---

### Post by oldfred on 2010-09-01
You can convert but have to manually create partitions:

HOWTO: migrate wubi install to partition by bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Old conversion LVPM, see Alternative Instructions 
[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

Use windows to shrink the  windows partition then use gparted to create a / (root) and swap partiitons.
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Mark Phelps on 2010-09-02
> **wilee-nilee said:**
> This is a wubi install I believe.

Sorry ... missed that.

OK, then install EasyBCD 2.0.x from the NeoSmart technology forums in Win7.

Then, open it and choose Ubuntu as the default selection.

---

### Post by phantom27 on 2010-09-02
I found a much easier solution!  

I reinstalled ubuntu, formating the entire drive!  Now I only have ubuntu! ...and it doesn't boot into win7  ;)

---

### Post by oldfred on 2010-09-02
I like your fix. Quick & simple and it really eliminates a big problem (as long as you can live without it). Sometimes withdrawal can be a bear.:)

---

### Post by phantom27 on 2010-09-04
No withdrawal...  I'm loving Ubuntu.  I've still got two machines with Win7, my desktop and my wife's laptop.  What I love about Ubuntu is how quick and snappy my netbook is now.  I even setup the multi-desktop cube changer and it doesn't slow down at all.  I love it.  It makes my netbook feel snappy, like a desktop.

---

