---
title: "Ubuntu 10.04 on VirtualBox crashed"
date: 2010-09-21
forum: General Help
---

### Post by RSASKA on 2010-09-21
Hello,

I installed Ubuntu 10.04 on VirtualBox, installed on top of a Mac so I can learn programming (studying for certification for my job). 

Just now, it went black, so I sent the power off signal. However, when I restarted, I keep getting the following error as shown in 01-error.png. When I enter help, it displays following commands shown in 02-error.png

Tried researching the problem myself, and found the following link


[http://ubuntuforums.org/showthread.php?t=295508](http://ubuntuforums.org/showthread.php?t=295508)

However, I am not sure if it applies in my case because this is on a virtual machine. And what am I supposed to mount?

I need to recover data I saved on this VM, re-installation is the very last resort.


Please guide.

---

### Post by RSASKA on 2010-09-21
I must add, the MacBook air does not have a CD drive, hence I am unable to boot a live CD. Is there something I can do with the ISO image.
 
Please advise. I really want to avoid reinstalling the VM and the programs on it.
 
Thank you.

---

### Post by anglican on 2010-09-21
> **RSASKA said:**
> I must add, the MacBook air does not have a CD drive, hence I am unable to boot a live CD. Is there something I can do with the ISO image.
 
Please advise. I really want to avoid reinstalling the VM and the programs on it.
 
Thank you.Luckily you don't need an actual CD drive to boot a VM from a live CD. Just download the iso image and add it to your VM (under storage). Then press [f12] when booting and choose the CD image to boot from.

H

---

### Post by RSASKA on 2010-09-21
> **anglican said:**
> Luckily you don't need an actual CD drive to boot a VM from a live CD. Just download the iso image and add it to your VM (under storage). Then press [f12] when booting and choose the CD image to boot from.

H

Hello,

I pressed function f12 and selected CD, which corresponds to the ISO and now it is booting, i.e. the background is dark-purple and the dots under "Ubuntu" become red, and then become white.

Approximately how long will this process take?

---

### Post by RSASKA on 2010-09-21
Hello,

Ubuntu 10.04 has been booting for the past hour. This doesn't seem normal and I have to turn off my computer for the day. Please advise next steps.

Nonetheless, I will try to save the state of the VM.

---

### Post by anglican on 2010-09-22
> **RSASKA said:**
> Hello,

Ubuntu 10.04 has been booting for the past hour. This doesn't seem normal and I have to turn off my computer for the day. Please advise next steps.

Nonetheless, I will try to save the state of the VM.No, I wouldn't expect that at all. You should get the Ubuntu installation menu with initially the "language choice" window superimposed. Once you select a language you should see the disk menu, something like (this is for the Xubuntu 10.04 alternate CD):
> Install Xubuntu
Check disk for defects
Test memory
Boot from 1st hard disk
Rescue a broken system
From which I'd choose "Rescue a broken system". You'll then see loads of text whizzing past before you see another language choice menu, then a locale choice, then a keyboard choice, then hardware gets detected and eventually you get offered a hard disk to mount as root. If this doesn't mount then I suspect your files may well be lost to you.

H

---

### Post by RSASKA on 2010-09-22
Hello,

Perhaps I am overlooking some steps, hence the difficulty.

Attached are screenshots of what I did, please advise:

01-settings then storage.png

I selected the VM, named Lucid_Lynx, went to settings then storage

02-replace vboxadditions with ubuntu ISO.png

Originally, the IDE had VirtualBoxGuestAdditions, which I replaced with the Ubuntu IS0

03-asks where to boot from.png

Upon startup, I press F12 and when it asks where to boot from I select CD-ROM by pressing "c"

04-keeps booting.png

Ubuntu keeps booting



Thank you for your guidance (and patience!)

---

### Post by anglican on 2010-09-23
> **RSASKA said:**
> 
Perhaps I am overlooking some steps, hence the difficulty.

...

Ubuntu keeps booting

...

Thank you for your guidance (and patience!)Well, I can't see where you're going wrong here! But you must be somewhere as the VM is clearly not booting from the CD but trying to boot from the VDI. Perhaps changing the device for the CD might help - though I can't see why that should make a difference. Maybe you should try creating a new VM, perhaps something in the settings for the existing one is causing a problem... it is very strange that you can't boot from a CD image as that should work even if the disk image is completely corrupt. Perhaps downloading a new iso image might also help - it could be that there's something wrong with yours.

H

---

### Post by migs73 on 2010-09-23
Install in the VM not working.
Trying to boot from Image on Virtual CD not working.
Same image file for both?

I would download a new image file and check it using this;
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

and then try again.

---

### Post by RSASKA on 2010-09-23
Hello,

Yes, I have used the same ISO image to re-boot. Did an MD hash and it is

9a95ed6f6ec38fb58c446dba1add6a08

which matches the one corresponding to ubuntu-10.04.1-desktop-i386.iso

Will download of a fresh copy of the ISO later today and try again...

---

### Post by RSASKA on 2010-09-23
Still no luck

When I used mini.iso, I didn't know what commands to enter


Will download a fresh copy and try again once more before deciding to throw in the towel....

---

### Post by RSASKA on 2010-09-24
Since I am on a short break, just for grinns, I replaced the IDE controller from the ubuntu ISO to the original VBoxGuestAdditions.iso

I started the VM, kept pressing F12 till it prompted the boot device. I selected 1 for Primary Master

The system loaded and warned there were errors. I pressed "I" for ignore.

I still want to understand what these errors are and how to fix them.

For now I will copy over my important files and save the state of the VM.

Please tell me how to make an ISO of the VM as a back-up.

---

