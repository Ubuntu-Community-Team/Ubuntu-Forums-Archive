---
title: "How do i find D: drive?"
date: 2012-07-02
forum: General Help
---

### Post by jondi11 on 2012-07-02
I used D: drive to install Ubuntu 12.04 , but i also have Music and Photos here that i would like to use on ubuntu, how do i get these? can't seem to find my drives. This being run alongside Windows vista on a laptop.

---

### Post by cortman on 2012-07-02
> **jondi11 said:**
> I used D: drive to install Ubuntu 12.04 , but i also have Music and Photos here that i would like to use on ubuntu, how do i get these? can't seem to find my drives. This being run alongside Windows vista on a laptop.

You say you had photos and music on the same partition you installed Ubuntu on?
In that case, your stuff is probably lost- installing an operating system means wiping all the old data off the drive it's installed on.
Or were you meaning that you'd like to get at your files on your Windows partition from Ubuntu? Please clarify.

---

### Post by dino99 on 2012-07-02
D: drive is a Windows spelling, with ubuntu (linux) drive are named /dev/sdx (x= a ->z) and partition /dev/sdxx (like sda1)

start gparted to see hdd details

my way for installation:  [http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by jondi11 on 2012-07-02
In used D: drive to install Ubunto, but i also had photos and Music on that drive, this is still running alongside Windows Vista. Can i find and open those files to use on Ubuntu?

Partitioned about 12gb

---

### Post by dino99 on 2012-07-02
> **jondi11 said:**
> In used D: drive to install Ubunto, but i also had photos and Music on that drive, this is still running alongside Windows Vista. Can i find and open those files to use on Ubuntu?

ubuntu can deal with ntfs partitions via the driver ntfs-3g (installed by default)

---

### Post by jondi11 on 2012-07-02
A bit more info please, newbie ,only just started to use this

---

### Post by dino99 on 2012-07-02
my way for installation:

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

and a lot more info via the links below ;)

---

### Post by jondi11 on 2012-07-02
Thats not telling me how i can get my music and photos though is it?

---

### Post by coffeecat on 2012-07-02
@jondi11, We need more information.

If you installed Ubuntu to what was your Windows D: partition using the live CD or live USB and the installer reformatted the partition for Ubuntu, then you have lost your files.

If, however, you used the wubi installer - that is you ran the wubi executable in Windows - and specified D: for your wubi Ubuntu installation, the installer would have created a virtual partition in D: for Ubuntu and  you will be able to access your files that are in D:

Open a terminal and post the output of this command:

```
df -h
```

We will then be able to see what sort of installation you have and advise. 

You can paste the output into your post by highlighting it with the mouse and right-click -> copy.

---

### Post by jondi11 on 2012-07-02
Yes the later. 
Here's the Terminal reading

Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       16G  6.4G  8.2G  44% /
udev            1.5G  4.0K  1.5G   1% /dev
tmpfs           592M  864K  591M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G  156K  1.5G   1% /run/shm
/dev/sda3        70G   34G   36G  49% /host
/dev/sda2        70G   57G   13G  82% /media/Acer
/dev/sda1       9.8G  7.6G  2.3G  78% /media/PQSERVICE
jondi11@ubuntu:~$

---

### Post by coffeecat on 2012-07-02
That's a relief. :)

Open a nautilus file browser, and in the left pane click on "File System". Now open the "host" folder which you will see in the main pane. You will now see the filesystem for the Windows partition in which you installed wubi Ubuntu. If it was the D: partition (which your output suggests) then you will see the contents of D:

---

### Post by jondi11 on 2012-07-02
do have to download nautilus file browser? Sorry if I'm dumb at this, new see

Found it and found music files, what do do to share with Ubuntu  or do copy

---

### Post by coffeecat on 2012-07-02
No problem. :) If you have standard Ubuntu, nautilus is the standard file browser. Simply open your home folder. That's the folder icon near the top of the launcher on the left.

---

### Post by jondi11 on 2012-07-02
see last edited post, cheers all
Do i share or copy files? if so how?

---

### Post by coffeecat on 2012-07-02
> **jondi11 said:**
> see last edited post, cheers all
Do i share or copy files? if so how?

Once you've opened your host folder, you can write to your D: partition from Ubuntu. So there's no real reason to copy. You use drag and drop in file browsers in Ubuntu just the same way as in Explorer in Windows.

---

### Post by jondi11 on 2012-07-02
Thanks think i've cracked it

---

