---
title: "Sound problems, partition problems."
date: 2010-04-12
forum: General Help
---

### Post by SirRedTooth on 2010-04-12
I have been having multiple problems for the past 5 months I have been using ubuntu. Very, very frustrating indeed.

Firstly, whenever I update I get these stupid errors in the terminal view (this has been happening from the moment I installed ubuntu for the first time):
[http://siteguides.net/1.png](http://siteguides.net/1.png)
[http://siteguides.net/2.png](http://siteguides.net/2.png)
[http://siteguides.net/3.png](http://siteguides.net/3.png)
^A view of all my partitions, the partition ubuntu on /dev/sda3 was supposed to be where ubuntu went, but it didn't work out. (That is not where ubuntu is)

Also the only two USB's i have plugged in is the wireless adapter and the receiver I need for my wireless mouse and keyboard

Also for some reason, sometimes a application (can be anything from VLC media player to firefox stops playing sound.
Usually there is atleast one application that can play sound (while all the others can't) but as of today I can't play any sort of sound from my computer. (I have rebooted over 5 times now).


Also, the Grub loader has been inundated with options that get added every once in a while when I update. Is there anyway to remove some of them?

Thanks for your time.

---

### Post by dandnsmith on 2010-04-12
According to the 3rd pic, sda3 is NTFS - you cannot get Ubuntu to install there without re-formatting it as Ext2,3, Reiserfs, FAT ...

I don't have a clue about the sound - there doesn't seem to be anything to base a guess on.

It's possible to edit the grub options - precise details depend on whether you use grub 1.x or grub 2.

---

### Post by SirRedTooth on 2010-04-12
> **dandnsmith said:**
> According to the 3rd pic, sda3 is NTFS - you cannot get Ubuntu to install there without re-formatting it as Ext2,3, Reiserfs, FAT ...

I don't have a clue about the sound - there doesn't seem to be anything to base a guess on.

It's possible to edit the grub options - precise details depend on whether you use grub 1.x or grub 2.
Yeah but can you solve the errors I have been getting in the first and second pic?

I am grub 1.x I think.

---

### Post by dandnsmith on 2010-04-18
Sorry - I've had to be absent for a while, so haven't commented further.

In png1: the errors refer to /dev/sdb1 - but nowhere is there any clue as to what device this is. The actual errors suggest an improperly sized/formatted - I cannot go further than that.

In png2: the errors seem to give a precise description of the errrors, and the steps to take - do you have any reason to doubt this?

The file you want is grub.conf or menu.lst - but perhaps that isn't the question you want answered.

---

### Post by lidex on 2010-04-18
What is the output of this command:
```
sudo fdisk -l
```
Why are we looking at gdebi? You said you had update errors; how about running these commands and posting the terminal output:
```
sudo apt-get update
sudo apt-get upgrade
```

---

