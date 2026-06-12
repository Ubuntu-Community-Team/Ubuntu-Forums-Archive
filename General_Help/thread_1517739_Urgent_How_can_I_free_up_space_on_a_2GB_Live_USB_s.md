---
title: "Urgent: How can I free up space on a 2GB Live USB stick running Ubuntu 10.04?"
date: 2010-06-25
forum: General Help
---

### Post by rmp73 on 2010-06-25
Hi,

I created a Live USB stick with 10.04 when it was released to see what Ubuntu was like.  Then I used that to install the full OS to my HDD.  I've since screwed up the system (see [http://ubuntuforums.org/showthread.php?t=1517540&highlight=gparted+nightmare](http://ubuntuforums.org/showthread.php?t=1517540&highlight=gparted+nightmare)) and so I'm back to using the Live USB stick to try and rectify things... However, it's now FULL and won't do anything anymore.

How can I free some space on the USB... [please help]

---

### Post by Penguin Guy on 2010-06-25
You could try Baobab ([COLOR="Green"]Applications -> System Tools -> Disk Usage Analyser[/COLOR]), that'll help you find a delete the files that are wasting the most space.

---

### Post by rmp73 on 2010-06-25
> **Penguin Guy said:**
> You could try Baobab ([COLOR="Green"]Applications -> System Tools -> Disk Usage Analyser[/COLOR]), that'll help you find a delete the files that are wasting the most space.

But I'm not sure which ones to delete... I believe the files in the persistent area are stored in a partition called casper-rw, which isn't mounted, nor can it be in that tool... So you can't clear it out - unless I missed something?

---

### Post by Penguin Guy on 2010-06-25
> **rmp73 said:**
> But I'm not sure which ones to delete... I believe the files in the persistent area are stored in a partition called casper-rw, which isn't mounted, nor can it be in that tool... So you can't clear it out - unless I missed something?
You could simply delete everything on the [FONT="Courier New"]casper-rw[/FONT] partition with no ill effects to the OS (although, obviously, all settings and data will be lost). I can't think of any other solutions.

---

### Post by C.S.Cameron on 2010-06-25
If the drive is only 2GB persistence is probably in a file named casper-rw.
You can delete this and the drive should now boot but without persistence.

If you actually have a partition named casper-rw, you can use gparted, (booting from the Live CD), to reformat that partition, or you can delete the stuff in it while booted from the Live CD or a Ubuntu computer.

---

### Post by rmp73 on 2010-06-25
> **C.S.Cameron said:**
> If the drive is only 2GB persistence is probably in a file named casper-rw.
You can delete this and the drive should now boot but without persistence.

If you actually have a partition named casper-rw, you can use gparted, (booting from the Live CD), to reformat that partition, or you can delete the stuff in it while booted from the Live CD or a Ubuntu computer.

What are the best COMMAND LINE prompts to enable me to do that?  I can boot into the Command Line on the HDD as my OS is on /dev/sda1 - I guess I'd need to mount the USB first?

---

### Post by C.S.Cameron on 2010-06-25
I don't do much command line stuff but I think it goes something like:
```
sudo rm casper-rw
```
if it is a file.

Not sure about how to remove everything in a partition if it is a casper-rw is a partition.

Hopefully someone that knows command line will lend a hand here.

---

