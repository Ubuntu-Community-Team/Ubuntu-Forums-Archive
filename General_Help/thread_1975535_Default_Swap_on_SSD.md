---
title: "Default Swap on SSD"
date: 2012-05-07
forum: General Help
---

### Post by traditionalist on 2012-05-07
I have Ubuntu 12.04 64 BIT running on my machine, and it installed a swap partition by default on my SSD.  I don't want a swap partition on my SSD  how can I move it to another disc?

Regards....Trad

---

### Post by oldfred on 2012-05-07
Comment out the entry in fstab and add a new entry for the swap you have on anther drive. Or replace old UUID with new.

#Edit fstab with your UUID:
sudo blkid -o list
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

# always run this to be sure you made no typos
#Verify entry is ok, if no errors it is:
sudo mount -a

---

### Post by traditionalist on 2012-05-07
> **oldfred said:**
> Comment out the entry in fstab and add a new entry for the swap you have on anther drive. Or replace old UUID with new.

#Edit fstab with your UUID:
sudo blkid -o list
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

# always run this to be sure you made no typos
#Verify entry is ok, if no errors it is:
sudo mount -a

Thanks very much, I will try that immediately. I am a total newbie to UBUNTU I have been using Windows for many years. It is taking time to get up to speed on a lot of stuff.

So I have to set up a swap partition on another drive first?  Best way to do that?  

Regards....Trad

---

### Post by traditionalist on 2012-05-07
This is what I get;

QUOTE

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid      0  0  
# / was on /dev/sdc1 during installation
UUID=271df674-47a4-4407-b0e8-51463b11cb2c  /            ext4  errors=remount-ro        0  1  
# swap was on /dev/sdc5 during installation
UUID=e8ca2bf4-5ee1-4959-ab98-e0ca8b0f3669  none         swap  sw                       0  0  
/dev/sdb1                                  /media/sdb1  ntfs  nls=iso8859-1,umask=000  0  0  

UNQUOTE

Not sure how to proceed further. I will try and read up on some more info, and get back if I have any problems.

Regards....Trad

---

### Post by traditionalist on 2012-05-07
Hmm...I can't do anything at all to that drive. Gparted simply returns errors ( Daemon inhibited)  if I try to do anything.

This is what I have;

[[IMG]http://img690.imageshack.us/img690/738/selection005b.png](http://img690.imageshack.us/i/selection005b.png/)

[[IMG]http://img191.imageshack.us/img191/5157/selection006v.png]("http://img191.imageshack.us/i/selection006v.png/")

Unfortunately I can't do anything.  Any ideas?  

Regards....Trad

---

### Post by oldfred on 2012-05-07
I only use gparted. But you cannot edit any mounted partition and that includes the extended and any mounted logical in the extended mounts the entire extended partition.

So you have to use a liveCD or make sure you have unmounted all the partitions you may want to  edit on another drive. With a liveCD it often mounts swap if found, so you have to click on the swap and right click swap-off.

It looks like you have deleted swap on the SSD, you can delete the extended and expand / if you want.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by traditionalist on 2012-05-07
Thanks!  I figured that.  I thought about this for a while and visualised various scenarios.  I came up with a very quick solution.  I had just run a complete backup of my system using remastersys and burned it to a DVD, and so I simply booted that and reinstalled using the whole disc and no swap area.  Worked like a charm!  Brilliant program!

Now I can set up a swap area on another disc.

Thanks a lot for all your help.

Regards....Trad

---

### Post by traditionalist on 2012-05-07
Just for info, this is what the disc looks like now, ( I removed some indices before I burned the remastersys custom iso.  Anyway, it worked really well and was pretty quick too;

[[IMG]http://img152.imageshack.us/img152/7135/selection001w.png](http://img152.imageshack.us/i/selection001w.png/)

Regards...Trad

---

### Post by oldfred on 2012-05-07
Glad you figured it out. Often good to have a backup.

Would you use screen shots and use the paper clip icon in the messge edit panel to upload. It makes viewing thread easier, thanks.

My SSD just to show upload.

---

### Post by traditionalist on 2012-05-07
> **oldfred said:**
> Glad you figured it out. Often good to have a backup.

Would you use screen shots and use the paper clip icon in the messge edit panel to upload. It makes viewing thread easier, thanks.

My SSD just to show upload.

OK. Sorry about that, I am used to using an external hoster.

Regards....Trad

---

### Post by dcstar on 2012-05-08
> **traditionalist said:**
> This is what I get;


```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid      0  0  
# / was on /dev/sdc1 during installation
UUID=271df674-47a4-4407-b0e8-51463b11cb2c  /            ext4  errors=remount-ro        0  1  
# swap was on /dev/sdc5 during installation
UUID=e8ca2bf4-5ee1-4959-ab98-e0ca8b0f3669  none         swap  sw                       0  0  
/dev/sdb1                                  /media/sdb1  ntfs  nls=iso8859-1,umask=000  0  0  
```


You **need **this to enable TRIM on your system otherwise your SSD performance will deteriorate:

```
UUID=271df674-47a4-4407-b0e8-51463b11cb2c  /            ext4  errors=remount-ro,**discard**       0  1
```

---

### Post by traditionalist on 2012-05-08
OK Thanks. Will try and set it up properly later today. Was having too many other problems to worry much about it.  I am getting there slowly though.

Thanks for the info.

Regards...Trad

---

### Post by oldfred on 2012-05-08
I forgot to include the trim command discard and used it for a bit. Then found this. He suggests not using trim command at all and just running the cleanup as a cron task daily.

[https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
hdparm -I /dev/sdX

Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)

fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed

Issues with OCZ Vertex II SSD and discard option
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives) - SSD
[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

---

### Post by traditionalist on 2012-05-08
Thanks again.  I am working my way through a mountain of info on all this.  I Have used Windows for a very long time, and all this is new as are some of the concepts.  It is quite difficult to forget a lot of Windows habits and learn completely new ways of doing things, especially in such a short time ( I have only been running this for a week).

Right now I am trying hard to stabilise my system even more and getting the basics set up as I want them.  I have completely reinstalled the system at least thirty times to date, and made a lot of mistakes due to lack of relevant knowledge, but my data is all backed up so I can afford to play around a bit.

Up to now I am impressed at what is possible with the right setup of a lot of stuff, but there are also a few things I don't like.  That would doubtless be true of more or less anything.  One thing that is obvious is the rather fragmented nature of the available information, can be very difficult to pin some stuff down, so every little helps.  It will take a while to get everything just right though.

Regards...Trad

---

