---
title: "Big help"
date: 2011-02-26
forum: General Help
---

### Post by rblloren on 2011-02-26
Hello!

I got a problem with my laptop with an ubuntu 10.10 OS.
Last thursday we went for dinner at Pizza's. I tried to connect to their wifi. While logging in to the internet, my laptop went dead and when i reboot my computer, all I can see was a blank screen and a
** BusyBox v1.15.3(Ubuntu …….)** ***(initramfs) ***. Could everybody please help. I badly needed the files from my computer ASAP. I tried to follow some steps in web, but it seems those were not working. Thanks.

---

### Post by Script Warlock on 2011-02-26
> **rblloren said:**
> Hello!

I got a problem with my laptop with an ubuntu 10.10 OS.
Last thursday we went for dinner at Pizza's. I tried to connect to their wifi. While logging in to the internet, my laptop went dead and when i reboot my computer, all I can see was a blank screen and a
** BusyBox v1.15.3(Ubuntu …….)** ***(initramfs) ***. Could everybody please help. I badly needed the files from my computer ASAP. I tried to follow some steps in web, but it seems those were not working. Thanks.

see if this can help..
[http://ubuntuforums.org/showthread.php?t=1682433](http://ubuntuforums.org/showthread.php?t=1682433)

---

### Post by rblloren on 2011-02-26
Thanks for the reply dude, 

Read the posts from the link you gave. I already inserted a burnt ubuntu10.10 file but still I cannot log-in to the computer to see the partition, still cant edit at GRUB and could not work on the terminal to change the /dev/sdax.
What should I do. Thanks much!

---

### Post by bcbc on 2011-02-26
I'm not sure what the problem might be...

But you need to get a live CD working to figure it out. You said when you boot from the 10.10 CD you still cannot login - normally you don't login it takes you direct to the desktop. So you might have a problem with that CD or you're not booting it correctly. 

Place the CD in the drive, press your bios boot options key, select to boot from CD, hit the space bar when you see the little keyboard and man icon in the bottom centre, then select language and Check Disc for Errors. Make sure it's ok - if not you'll need to burn another. Then reboot into it again and "Try without installing".
After that you can run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results.

---

### Post by rblloren on 2011-02-27
Hi there bcbc!

Thanks for the reply. I did run the my computer with an ubuntu 10.10 cd. Was able to work on the trial version. I would like to ask how could I run my bootinfoscript? i tried working on the terminal and had sudo fdisk -l, I bet what shown up was my partition:

/dev/sda1 1 38149 306425856 83 Linux

What could be the next step? Still dont know hao to access my bootinfoscript. 
Thanks!

---

### Post by bcbc on 2011-02-27
> **rblloren said:**
> Hi there bcbc!

Thanks for the reply. I did run the my computer with an ubuntu 10.10 cd. Was able to work on the trial version. I would like to ask how could I run my bootinfoscript? i tried working on the terminal and had sudo fdisk -l, I bet what shown up was my partition:

/dev/sda1 1 38149 306425856 83 Linux

What could be the next step? Still dont know hao to access my bootinfoscript. 
Thanks!

The link in my previous post explains how to download and run the bootinfoscript.

---

### Post by rblloren on 2011-02-28
> **bcbc said:**
> The link in my previous post explains how to download and run the bootinfoscript.

Hi there BcBc!
what I did was that i downloaded the the bootinfoscript from the other other computer and transferred to my laptop. Then followed the steps on the terminal. What I got was SEARCHING SDA1 FOR INFORMATION....

Will this take long? What could I do for the meantime? 
I already had my partition information by typing sudo fdisk -l.

---

### Post by bcbc on 2011-02-28
It doesn't usually take very long. Run the disk utility and see if it reports any disk errors (Tools, Administration, Disk utility).

What's the output of (assuming you installed using the default ext4 fs):

```
sudo mount -t ext4 /dev/sda1 /mnt
```

---

### Post by rblloren on 2011-03-03
Hello BCBC, 

I already run the disk utility what I noticed was that my harddisk was not mounted. So I tried to mount it manually by clicking the mount icon, yet it took a lot of time even now I still am waiting for the result. This very slow response, could this be due to the ubuntu copy I burnt in my CD? I also tried to do what you told me to type on my terminal but still the terminal had no response just a blinking bar. Same with  what happened with my bootinfoscript rundown. What should I do? I really need your help and expertise. Thanks!!!

---

### Post by bcbc on 2011-03-03
It sounds like your disk is damaged. Doesn't the disk utility report anything on the drive (not the partition?)  Or maybe it's just the partition that's corrupted, but I'm not sure why 'mount' shouldn't just report an error in that case, rather than hanging.

I'm not really qualified to give advice on this, but this is what I might do.

Taking a cautious approach (assuming you don't have any backups and this is a recovery mission) - plug in an external USB drive and take a low-level image backup of your internal drive using something like *dd*
Install testdisk from the live CD (sudo apt-get testdisk) and run it's partner utility [photorec]("http://www.cgsecurity.org/wiki/PhotoRec") to recover as much personal data as you can. Photorec can run on damaged drives.

Then try fsck'ing /dev/sda1

Maybe someone else can jump in with some advice.

---

### Post by rblloren on 2011-03-03
> **bcbc said:**
> It sounds like your disk is damaged. Doesn't the disk utility report anything on the drive (not the partition?)  Or maybe it's just the partition that's corrupted, but I'm not sure why 'mount' shouldn't just report an error in that case, rather than hanging.

I'm not really qualified to give advice on this, but this is what I might do.

Taking a cautious approach (assuming you don't have any backups and this is a recovery mission) - plug in an external USB drive and take a low-level image backup of your internal drive using something like *dd*
Install testdisk from the live CD (sudo apt-get testdisk) and run it's partner utility [photorec]("http://www.cgsecurity.org/wiki/PhotoRec") to recover as much personal data as you can. Photorec can run on damaged drives.

Then try fsck'ing /dev/sda1

Maybe someone else can jump in with some advice.


Really thanks for your kind replies. Well, as far as I can remember, when I was connecting to a network all I saw before the system went off were lock icons on my files, may be these were just to protect my files, then I can no longer log-in to ubuntu on my desktop. I also found through my curiosity that my system harddisk was no longer mounted and there is no longer KERNEL on my system. What could be your opinion? If worse comes to worst, do you advise to reformat my computer? Thanks

---

### Post by bcbc on 2011-03-03
> **rblloren said:**
> Really thanks for your kind replies. Well, as far as I can remember, when I was connecting to a network all I saw before the system went off were lock icons on my files, may be these were just to protect my files, then I can no longer log-in to ubuntu on my desktop. I also found through my curiosity that my system harddisk was no longer mounted and there is no longer KERNEL on my system. What could be your opinion? If worse comes to worst, do you advise to reformat my computer? Thanks
Well if you've recovered as much as you can, and all repair attempts fail, then sure - not much else to do. 
But if the problem was caused by a hard drive fault, you're probably going to need a new one. 
And if the problem wasn't caused by the hard drive, you might have the same problem again.

---

### Post by rblloren on 2011-03-03
> **bcbc said:**
> Well if you've recovered as much as you can, and all repair attempts fail, then sure - not much else to do. 
But if the problem was caused by a hard drive fault, you're probably going to need a new one. 
And if the problem wasn't caused by the hard drive, you might have the same problem again.

How will I know that the caused of this problem is by the hard drive? :(

---

### Post by bcbc on 2011-03-03
If your hard drive is toast - you probably won't have any luck reformatting it.

---

### Post by rblloren on 2011-05-02
> **bcbc said:**
> If your hard drive is toast - you probably won't have any luck reformatting it.
 
 
Hello BCBC, need your expertise again, i hope you could give a reply. yesterday I upgraded my computer to ubuntu 11.04 from 10.10. Everything went well, but when i rebooted my system, the launcher and tskbar panel were gone all i can see were icons of my folders. How i can fix this? HOpe you could give help. Thanks!

---

### Post by bcbc on 2011-05-02
> **rblloren said:**
> Hello BCBC, need your expertise again, i hope you could give a reply. yesterday I upgraded my computer to ubuntu 11.04 from 10.10. Everything went well, but when i rebooted my system, the launcher and tskbar panel were gone all i can see were icons of my folders. How i can fix this? HOpe you could give help. Thanks!

Hi, are you referring to the new Unity interface (with the Dock on the left?). If you want the classic gnome desktop manager, logout, click on your username and before entering your password, look on the bottom and change the session from "Ubuntu" to "Classic". Everything should look the same as before.

---

### Post by rblloren on 2011-05-02
> **bcbc said:**
> Hi, are you referring to the new Unity interface (with the Dock on the left?). If you want the classic gnome desktop manager, logout, click on your username and before entering your password, look on the bottom and change the session from "Ubuntu" to "Classic". Everything should look the same as before.

Thanks BcBc! Got it! :D

---

