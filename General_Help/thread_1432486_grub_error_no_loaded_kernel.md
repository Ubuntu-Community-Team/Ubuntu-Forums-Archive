---
title: "grub error: no loaded kernel"
date: 2010-03-17
forum: General Help
---

### Post by Estela on 2010-03-17
I have Ubuntu installed in my machine, I also have Windows Vista.
I have been using Ubuntu perfectly well, today I received the following message when chose to boot Ubuntu:
**GNU GRUB version 1.97 beta 4**
**[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/flies completions]**
**sh:grub>**
 
When I wrote: boot, it says:
**error: no loaded kernel**
 
Any ideas how to solve this? Thanks in advance.

---

### Post by Jeff Anthony on 2010-03-17
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

sudo grub-setup '(hd0)'

---

### Post by crash20 on 2010-10-15
I use Ubuntu 10.10 partition with Win7, and after updating last night, I turned on my laptop this morning to discover the same GRUB issue. I try using the boot command, but I get error: no loaded kernel.

I visited the site mentioned above, but the problem is that my laptop doesn't have an optical drive, nor do I have a usb-connected one. So reinstallation through a liveCD isn't an option for me. Are there any other methods I can try without severely risking my computer? 

This is the second time now I've had kernel issues with Ubuntu, the firs time several months ago I also had an issue where it said there was no kernel, and then I eventually had to get my whole computer reformatted which took days :( I really like linux ubuntu, but if I keep getting serious problems like this, I don't know if I would continue using it...

---

### Post by hijataka on 2010-10-19
Hello,
I got the same problem as crash20.

> **[Minimal BASH-like line editing is supported. For the first word, TAB  lists possible command completions. Anywhere else TAB lists possible  device/flies completions]**
**sh:grub>**
 
When I wrote: boot, it says:
**error: no loaded kernel**

I installed Ubuntu 10.10 parallel to WinXp with wubi.
One day after updating and restarting the system I had the problem with grub...
When I boot with supergrub2 he doesn't recognize ubuntu only XP.
I already read loads of threads but I just can't boot anymore :(
Somebody got an idea or a useful link?

---

### Post by k0brakai on 2010-11-30
I have the same problem right now, My laptop battery completely discharged and the laptop just turned off. I have no CD drive so re-install not an easy option for me, plus i want my data. 

Any one got an answer for this one???

---

### Post by ozogha on 2011-05-25
Problem: 
Windows 7 VMware player Ubuntu 
during upgrade to 11.04 Narwhal
I got the before mentioned message, Ubuntu couldn't boot, can't find the kernel. 

Solution:
Somebody who knows linux very well helped me. 
Booted ubuntu using any *.iso image, he used: 
 ubuntu-11.04-beta2-desktop-i386.iso
then opened a terminal
grub.conf file was corrupted. He fixed that file.
Now I am back to normal. 
This is very bad, for somebody who don't know linux couldn't have fixed this. 

Best. haluk.ozoguz

---

### Post by witeshark17 on 2011-08-01
Can you please explain the details on how this was done? This post needs the steps that worked. Where was the grun.conf located and what was done to fix the corrupted issue?

---

### Post by insanity2k7 on 2011-11-01
This is actually super easy to fix, at least for the server version.  Just boot an 11.04 install disc and pick Recovery Mode from the boot menu.  OK through until you get to the "what do you want to do" menu and pick the Reinstall grub option.  It will list what your drives are.  In mine and probably most cases /dev/sda is the one you want.  Takes two seconds, reboot, and you should be good to go.  Hope this helps someone.

---

### Post by witeshark17 on 2011-11-02
Thanks for the reply. I have everything all good now.

---

### Post by oldos2er on 2011-11-02
Since your problem seems solved we'll let this thread go back to sleep.

---

