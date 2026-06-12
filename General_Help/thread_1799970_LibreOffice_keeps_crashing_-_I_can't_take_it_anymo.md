---
title: "LibreOffice keeps crashing - I can't take it anymore"
date: 2011-07-08
forum: General Help
---

### Post by BravoDelta65 on 2011-07-08
I've been a long time linux & Ubuntu fan/user. Since the clean install of 11.04, LibreOffice keeps crashing. No day would go past when using either Writer or Calc, that it will not crash. (I think OpenOffice had same issue on Ubuntu 10.10 but only later on in the cycle.)

The recovery function works, but it's now beyond a joke to continue to work in such a way, given that I have used Linux exclusively.

I develop web apps on Ubuntu, but am seriously thinking of going over to Windows 7 or even OSX if this continues much longer.

I have posted and asked for help on this forum once before but received no help.

If I can't get this issue resolved, I'm going to stop using Linux, which I do not want to do.

If it's any help, when searching for clues to issue on this forum and others, people mentioned a 'seg fault', this might be the issue I have, as I think I saw this reported on one of the error logs. I think a seg fault may have something to do with memory, but I don't know for sure.

Can anybody help?

---

### Post by grahammechanical on 2011-07-08
My first point is this.

Openoffice and Libreoffice are not produced by Ubuntu. If you have problems with Libreoffice crashing, then do not blame Ubuntu.

Secondly, this is a community forum. We do not know all the answers. In a way it is self help not customer service. It most definitely is not the customer service department of anything or anyone. If  you do not get any help it is because no one who has seen you post has any help to give.

Third, if you really think that the problem is caused by a seg fault then read this link

[http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)

Note, the introduction.

My suggestion (and it can only be a suggestion) is that you (a) back up any document/file that you do not want to loose. (b) you reinstall Ubuntu and Libreoffice formatting the partitions in the process.

In my ignorant opinion, I think that there is some conflict in the Libreoffice configuration files, settings and libraries that is messing up the way that Libreoffice is working.

A clean install will remove old configuration files and libraries and install fresh ones and I have found that this often solves these kinds of problems.

Regards.

---

### Post by Ad@m on 2011-07-08
Can you run memtest?

LibreOffice / OpenOffice is in my view a very stable piece of software and I am therefore inclined to believe you have a hardware problem.

---

### Post by BravoDelta65 on 2011-07-08
> **Ad@m said:**
> Can you run memtest?

LibreOffice / OpenOffice is in my view a very stable piece of software and I am therefore inclined to believe you have a hardware problem.

Hi Ad@m

how do I run memtest? do I need to 'sudo apt-get install'?

BTW - LibreOffice is the only software that crashes on this machine.

---

### Post by frncz on 2011-07-08
BTW - LibreOffice is the only software that crashes on this machine. 

Perhaps LibreOffice is the only application that intensively accesses a particular partition?

---

### Post by Erik1984 on 2011-07-08
> **Orbius Maximus said:**
> Hi Ad@m

how do I run memtest? do I need to 'sudo apt-get install'?

BTW - LibreOffice is the only software that crashes on this machine.

You can perform memtest in GRUB before Ubuntu boots. (hold shift when booting to enter the GRUB menu).

---

### Post by Sef on 2011-07-08
Either go into it at start up or download it [here]("http://memtest86.com/") and run it as a live cd.

---

### Post by BravoDelta65 on 2011-07-08
Thanks guys.

When I run memtest, what am I looking for, or will that be self evident by any message that appear on the screen?

---

### Post by john j jumpsticks on 2011-07-08
I'm having the same problem with LibreOffice Writer and have noticed a message once or twice upon boot-up that says something like it can't recognize the swap partition and something else about mounting. The message pops up and disappears pretty quickly so I was unable to write it down. Does any one know if this swap/mounting problem would cause LibreOffice to crash and how I might fix it?

BTW I did a clean install with 11.04 and just let the installation CD do whatever partitioning and formatting that it does automatically.

---

### Post by IWantFroyo on 2011-07-08
Hmm. That's weird. The only crashing problem I've ever had with OpenOffice/LibreOffice was back when I built my own computer and put 10.04 on it. Turns out my chipset voltage was low.

Try a clean installation, and test LibreOffice before and after installing updates.

---

### Post by BravoDelta65 on 2011-07-08
@John

I have Conky running on my machine, and with LibreOffice Writer running, and a few other apps and browser, My swap partition usage doesn't rise above 15%, and my RAM usually remains below 50%.

---

### Post by CoolJohnB on 2011-07-08
I to did a clean install of 11.04 I don't have any partitions except for the swap file which was done automatically on install.  With regard to Libreoffice I haven't had any problems, I have though upgraded it on a regular basis and am now on version 3.4.1, maybe if you do an upgrade this will help solve the problem.

When upgrading I removed Libreoffice completely using Synaptic and did a new install using the downloaded .deb files.

Hope that helps.

---

### Post by john j jumpsticks on 2011-07-09
I've uninstalled all of LibreOffice and re-installed Writer and so far it seems to be working fine. You could do the same thing with the whole LibreOffice suite but I didn't see the point considering Writer is the only office program that I regularly use. I'll let you know it it starts crashing again.

---

### Post by BravoDelta65 on 2011-07-09
> **john j jumpsticks said:**
> I've uninstalled all of LibreOffice and re-installed Writer and so far it seems to be working fine. You could do the same thing with the whole LibreOffice suite but I didn't see the point considering Writer is the only office program that I regularly use. I'll let you know it it starts crashing again.

Thanks John, I appreciate that.

---

### Post by Ad@m on 2011-07-10
Sorry for not being very clear concerning memtest.

When running memtest you are looking for memory errors, the screen will display red lines of text indicating an error.

Only let memtest run for 1 complete pass, that may take 30 mins or more depending on your setup. Anything beyond is straying into stress testing. However if memtest throws up any errors, stop it straight away as there is no point letting it continue to run.

What memtest essentially does is to write various patterns to your memory, then compare if it is the same to what was written.

---

