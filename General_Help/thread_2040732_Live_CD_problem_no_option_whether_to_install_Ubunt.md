---
title: "Live CD problem: no option whether to install Ubuntu on its own or not"
date: 2012-08-11
forum: General Help
---

### Post by rima on 2012-08-11
Hello, I have quite a curious problem, so bear with me if you can.

I have Windows XP SP2 system with AMD Sempron 140 Processor. I have two NTFS partitions (C:, with abou 110GB free, and D:, which is empty, and has about 111GB free). BTW it's a 'classic' desktop computer, NOT a laptop).

I burned the 701MB ISO image to a 700MB CD. It boots into LiveCD very well and very fast, and so far has been very impressed with how it's been working on the computer in the LiveCD envoirnment. Everything works fine and recogonizes my hardware well. Happy with what I saw, I want to install Ubuntu on its own, without Windows. However, I have run into some sort of a strange problem.

When I click on 'Install Ubuntu 12.04' it prompts me to choose my language. OK. Next, it asks me whether downloads should be installed, if the computer is connected to Internet, if there's 4GB free on the disk etc. 

Soon after I click 'Next', I should expect to choose whether to install Ubuntu alongside Windows or on its own. Instead of that a partition screen comes up straight away.

It's empty. 

Nothing's written on it. I'm unable to click on any buttons below it as well. The only options that I have is either to cancel the installation, or install Ubuntu (when I choose the second option, a dialog box pops up saying no partition's been set or similar).

What's gone wrong? Everything works fast and nice, but I'm unable to install the system itself!! I tried burning the disk again but it does the same thing with the 4.7GB CD-R that I have. 

So...what's wrong?

---

### Post by ajgreeny on 2012-08-11
Check the md5sum of the .iso file you have with those listed at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")

You can find all the details of how to do that as well at the same site, using the links on the page.

---

### Post by rima on 2012-08-12
I totally forgot to do that! Thanks for remainding me

---

### Post by rima on 2012-08-12
bump

I checked the md5sum. It's the same, so I don't know what is causing the problems.

---

### Post by jim_deadlock on 2012-08-12
You could try manually resizing your Windows partition using Gparted off the live CD to leave some free space for Ubuntu (or simply delete the empty partition?) and see if that makes any difference to your install.

---

### Post by rima on 2012-08-12
I googled lots about that but my mind is still blank. What do I do? How do I do it?

---

### Post by jim_deadlock on 2012-08-12
Just run your live CD and start up the Gparted program from the apps menu. Right-click your partition and do Resize/move (or delete) then click the Apply button at the top (green tick). It's very easy to use.

Once you've done that, shut down Gparted and run the install and see what happens.

---

### Post by oldos2er on 2012-08-12
Before you start changing partitions, make sure you have backups of any data you don't want to lose.

So that we can get a look at what's going on with your partitions, could you run the bootinfo script and post the results here? You can run it from the LiveCD. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

