---
title: "VirtualBox OSE problems"
date: 2011-02-06
forum: General Help
---

### Post by Spyderkid on 2011-02-06
I'm trying to do an Ubuntu virtual box. When I boot it up with the DVD i get lots of errors and stuff about unknown user ID so it gets the login screen and asks for a username and a password for which whatever I try doesn't work.

Any Ideas?

---

### Post by Spyderkid on 2011-02-06
{EDIT} ignore this post, sorry for the inconvinience.

---

### Post by Spyderkid on 2011-02-06
Here are some screenshots hope they help.

Ignore last post the screenshots didn't upload properly

---

### Post by Spyderkid on 2011-02-06
Also how can I make My VirtualBox boot from a USB? it only has options for CD, HardDrive and Network?

---

### Post by Spyderkid on 2011-02-06
Can anyone help?

---

### Post by [Snc] on 2011-02-06
Hello!

1. If you want USB to somehow work, don't use Virtualbox OSE, USB support is not included in Open Source Edition yet!
So jump to the Virtualbox page and download and install the non-OSE edition...

2. when creating a virtual drive, give it more space, make it 640Gb for example :) 
- select create a new hard disk
- select "*Dynamic expanding storage*"
This way, the new hard disk image will only be as big as there is data on it.

3. (*from the images*) SquashFS is something normally a Live CD/USB uses. Reboot, press F12 (when the VB bios gives you that option) and select 'c' for CD rom, make sure that the Ubuntu ISO is mounted, or the CD/DVD is in the tray, then select 'Install' instead of 'try' (i guess you selected try, if this is not the case, correct me ;))

4. VB config:
- Enable any virtualization, your host enables :)
- If you have a quad processor, give the guest 3 cores (IMHO ;))

well ... I can't remember of anything else :)

---

### Post by [Snc] on 2011-02-06
PS. I have USB enabled in Virtualbox, but in the boot menu, there is no USB option, so i guess it cannot be done.

---

### Post by Spyderkid on 2011-02-06
Ill keep the 8GB space and the 1 core but thanks for the info

---

### Post by [Snc] on 2011-02-06
hehehe :) did anything help, did it get you anywhere further?

---

### Post by Spyderkid on 2011-02-07
The problem was the installing from the DVD, it was the same with my acctual computer so I just used the .ISO image instead :)

---

### Post by garyjmellor on 2011-02-08
USB support is now working in VirtualBox OSE (4.0.2 r69518 ). See my post here (dated 08/02/2011):
 
[http://ubuntuforums.org/showthread.php?p=10439282#post10439282](http://ubuntuforums.org/showthread.php?p=10439282#post10439282)

---

### Post by Spyderkid on 2011-02-09
I don't seem to have an extensions button for what it says on your thread which you posted, sorry for posting on both meant to post on this one :)

---

### Post by [Snc] on 2011-02-09
> **garyjmellor said:**
> USB support is now working in VirtualBox OSE (4.0.2 r69518 ). See my post here (dated 08/02/2011):
 
[http://ubuntuforums.org/showthread.php?p=10439282#post10439282](http://ubuntuforums.org/showthread.php?p=10439282#post10439282)

Realy :)))))) I didn't know ... its hard to follow all the software one uses... I know, last time I bothered with this it wasn't supported.

So I Use VB 3.2.12 r68302, are there any great new features in V4.0.2, should I switch?

---

### Post by [Snc] on 2011-02-09
[QUOTE=garyjmellor]EDIT: I forgot to add, my host machine does not support virtualisation  (I wanted a 64-bit Maverick guest) but I still got this working. I did  not need to add myself to the vboxusers group either and, as mentioned  used the OSE not the paid-for version of VirtualBox.[/QUOTE]

I Also did not pay for VirtualBox, nor stole it (piracy sux ***) I just don't get the source with it. Well i will look into V4 anyways...

---

### Post by Spyderkid on 2011-02-12
So do you know how to enable USB on virtual box OSE?

---

### Post by williamts99 on 2011-02-12
> **'[Snc] said:**
> PS. I have USB enabled in Virtualbox, but in the boot menu, there is no USB option, so i guess it cannot be done.

Not directly booting from USB, it's not in the 'virtual bios', but you can use the PLOP boot manager.
[http://www.plop.at/en/bootmanagerdl.html](http://www.plop.at/en/bootmanagerdl.html)

---

### Post by Spyderkid on 2011-02-12
I don't need to boot from USB anymore but i need to copy a couple of files to a USB so anyone got any ideas?

---

### Post by ScottishGirl on 2011-03-14
I am using Ubuntu 10.10 and I can't seem to install Fedora 14 in virtualbox-ose.   I go through the install program successfully, but after restarting Fedora to complete the installation it reboots and starts the installation procedure all over again.

Any Ideas how to fix this.  I have managed to get Mandriva installed and working fine.

Stephanie

---

### Post by ScottishGirl on 2011-03-14
I get the following message: "A crash in the kernel package has been detected."

---

### Post by Spyderkid on 2011-03-15
its an error in your installation disk then not virtual box

---

