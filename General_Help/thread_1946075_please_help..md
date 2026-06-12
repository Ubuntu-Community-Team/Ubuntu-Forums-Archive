---
title: "please help."
date: 2012-03-24
forum: General Help
---

### Post by mcm42491 on 2012-03-24
i installed ubuntu to try over win. 7 and i honestly dont like it. i dont want 7 back but i bought a coppy of xp i want to put on. i tried to install it like every outher os i have worked with but it just comes up with windows has been shut down after the windows installer says starting windows. i really just want to completely get rid of this os on my labtop and put on xp.

---

### Post by MG&amp;TL on 2012-03-24
You might be better served on another forum; none of us here are Xp experts. (pardon the pun)

You could always try formatting the drive with gparted or similiar-it might be the windows installer doesn't like partitions.

---

### Post by mcm42491 on 2012-03-24
this new os is just so forign to me i have no idea how to format it. if i could just completly format the hard drive im shure i could get xp back on but i have no idea how to do that on this os.

---

### Post by MG&amp;TL on 2012-03-24
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Or you could install gparted in Ubuntu.

We do have a "try Ubuntu" option for a reason. ;)

---

### Post by mcm42491 on 2012-03-24
> **MG&TL said:**
> [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Or you could install gparted in Ubuntu.

We do have a "try Ubuntu" option for a reason. ;)
  lol yea well i had a bad version of 7 and just wanted it gone. hurd good things about ubuntu so i tried liked it initionaly and installed it. and figgured if i dident like it it would be no big deal to install windows over it. but i tried and it seems imposible lol

---

### Post by mcm42491 on 2012-03-24
i installed it thru ubuntu and its saying only a root can run it? i dont understand. im the administrator on here?

---

### Post by MG&amp;TL on 2012-03-24
Yeah, see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Alt-F2, then:

```
gksu gparted
```

should work.

Okay, you are forgiven. :D

---

### Post by mastablasta on 2012-03-24
you need to boot from the LIVE disk (the CD/USB you used to install it-> select try it on boot. Then run gparted unmount the disk and delete all partitions. you can also reformat it to whatever format oyu like (probably NTFS (Since you want to get XP on it) and then reboot, take outr the LiveCD and now stick in the windows XP cd and reboot. do the install. 

another option would be to use fdisk on your XP install CD only i am not sure if it can see EXT4 (ubunus) parititons. however if i sees the drive it could also delete partitions, drive is then reformated during install.

---

### Post by Linux_junkie on 2012-03-24
> **mcm42491 said:**
> i installed ubuntu to try over win. 7 and i honestly dont like it. i dont want 7 back but i bought a coppy of xp i want to put on. i tried to install it like every outher os i have worked with but it just comes up with windows has been shut down after the windows installer says starting windows. i really just want to completely get rid of this os on my labtop and put on xp.

You say you don't like Ubuntu, I am assuming that you were using the Unity desktop in Ubuntu and its that you don't like.   

Another option for you is to install the Kubuntu desktop and remove the Ubuntu desktop this will install the K desktop and its packages. The k desktop looks very  similar to Windows Vista/7 desktop.

Open the terminal and type the following
```
sudo apt-get install kubuntu-desktop
```
```
sudo apt-get remove ubuntu-desktop
```

---

### Post by wildmanne39 on 2012-03-24
+1 > for you need to boot from the LIVE disk (the CD/USB you used to install it-> select try it on boot. Then run gparted unmount the disk and delete all partitions. you can also reformat it to whatever format oyu like (probably NTFS (Since you want to get XP on it) and then reboot, take out the LiveCD and now stick in the windows XP cd and reboot. do the install. 


The problem is that xp can not see the linux partitions and after you create the ntfs using what mastablasta suggessted it should work.

Also make the NTFS partition primary.
Thanks

---

### Post by collisionystm on 2012-03-24
> **mcm42491 said:**
> i installed ubuntu to try over win. 7 and i honestly dont like it. i dont want 7 back but i bought a coppy of xp i want to put on. i tried to install it like every outher os i have worked with but it just comes up with windows has been shut down after the windows installer says starting windows. i really just want to completely get rid of this os on my labtop and put on xp.


You are getting this  message because XP does not recognize your hard drive. It is because it needs the SATA drivers. Your computer is too new for it.

You need to have the sata drivers on a usb drive and during XP setup press F6 to specify additional drivers. 

If you have access to another computer, I suggest using nLite to slipstream the sata drivers into a custom XP disk.

---

