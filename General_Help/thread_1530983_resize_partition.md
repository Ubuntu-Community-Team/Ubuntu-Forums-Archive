---
title: "resize partition"
date: 2010-07-14
forum: General Help
---

### Post by luvgirl12345 on 2010-07-14
[IMG]http://a.imageshack.us/img824/6977/screenshotbl.png[/IMG]


I would like to resize my ext4 partition (I DONT want to format it... unless you know a good way to back it up and restore it later) 

Luvgirl12345

---

### Post by nmaster on 2010-07-14
> **luvgirl12345 said:**
> ... unless you know a good way to back it up and restore it later) 

Luvgirl12345

this is pretty good: [http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

you could archive the partition you have and then restore to the new one.

---

### Post by luvgirl12345 on 2010-07-14
So I could archive it and put it on a External HD, then format and resize the partition and restore the archive... have you tested/used FSArchiver??

luvgirl12345

---

### Post by drs305 on 2010-07-14
I've used fsarchiver often and it's always been very reliable for me. It's on most of the system rescue type cd's (systemrescuecd, gparted cd, etc).

You image isn't working for me.

For just moving/changing the / partition, I wrote a guide about it in response to a bug back in Jaunty. The second half of the post provides some tips if you decide to just use gparted to move things around.
[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by luvgirl12345 on 2010-07-14
Im on a ubuntu 10.4 liveCD. Im guessing I have to download some kind of special rescueCD. I am going to  boot into my main installation and download a liveCD with FSArchiver installed. Will report back soon.

---

### Post by drs305 on 2010-07-14
luvgirl12345

If you are still here, fsarchiver should be in the universe repository and you can run it from the LiveCD. I normally am doing other maintenance and thus prefer the 'rescue' CDs since they boot faster and have more of the utilities I sometimes need. 

You should be able to use the LiveCD. If fsarchiver isn't on the LiveCD, you can download and install it from there if you wish.

---

### Post by luvgirl12345 on 2010-07-14
hmm that was to "late" but if I can do that with a CD (read only) That would be great. Will try that instead of downloading another OS and burning that.

Luvgirl12345

---

### Post by luvgirl12345 on 2010-07-14
Ok i downloaded fsarchiver and started it from the terminal. I need a bit help xD. I have an ExtHD from verbatim. If I type [COLOR=Red]fsarchiver savefs[/COLOR] would that be enough?? where does the saved archive go after saving it? 

Thanks for your help, luvgirl12345

---

### Post by drs305 on 2010-07-14
Here are the two commands I use to save and restore my partitions:

Save (the /dev/sda5 partition to mountpoint /mnt/temp on another partition). The mount point can be on any partition/device except the one you are trying to backup.  I had to create this mount point. The file name is lucid.fsa. 
```
fsarchiver savefs -z 3 -v /mnt/temp/lucid.fsa /dev/sda5
```
It uses a compression level of 3 and shows me the files as it archives them.

Restore file to sda5:
```
fsarchiver restfs /mnt/temp/lucid.fsa id=0,dest=/dev/sda5
```

You might also want to record the current state of your partitions, even though you are about to change them.

```
dd if=/dev/sda of=/mnt/temp/mbr.512.img bs=512 count=1 
```

---

### Post by luvgirl12345 on 2010-07-14
Ok first the savefs command:

```

fsarchiver savefs /media/VERBATIM/lucid.fsa /dev/sda5

```

default compression is 3 so adding a -z switch is not necessary (if Im right...)

The restore command would be:

```

fsarchiver restfs /media/VERBATIM/lucid.fsa id=0,dest=/dev/sda5

```

Is that correct??
I also saw that you used a temp folder... would that be better than an extHD??

Sorry that im asking so much but I really want everything to go smooth and not lose all my settings and files...

---

### Post by drs305 on 2010-07-14
I don't remember the default compression level, TBH. I've used 3 for quite a while but switch to others from time to time based on the compression level I desire and/or which method I want to use for compression.

Your mount point is fine - no need to change it. Just make sure the device is actually mounted on the mount point before you begin.

I notice you didn't use the -v switch, which is fine. Without it, however, you will get no feedback. You will press ENTER and the terminal will just sit there until the job is complete, which could take some time (mine is about 15 minutes usually for a 20GB ). Note it depends on the content size, not the partition size.

---

### Post by luvgirl12345 on 2010-07-14
about the -v switch: I thought this was for pros and i didn't need it. I just started the process and will report back later. 

Im just wondering: this cant f##k something else up right?? like grub or something.

update: Ok I need to try it with the temp folder... forgot that the HD  was formated with FAT (not my HD so Im not allowed to format it...)

---

### Post by drs305 on 2010-07-14
> **luvgirl12345 said:**
> 
Im just wondering: this cant f##k something else up right?? like grub or something.

If the partition is resized it will probably keep the same UUID. If you delete it and create a new one it will produce a new UUID that will not match what is in your system files.

You can either reinstall grub-pc via the LiveCD or make sure the UUID of the new partition matches the old one (if it changed).

You can get the original UUID by running the following command before you destroy the current partition, or copy it from the existing /boot/grub/grub.cfg or /etc/fstab file.

Run the following command once you have created a new partition and note if the UUID has changed. Run the second command if the UUID changed, using the original UUID.
```

sudo blkid
sudo tune2fs -U [COLOR="DarkRed"]<oldUUID>[/COLOR] /dev/sd[COLOR="DarkRed"]XY[/COLOR]
```

Example:
```
sudo tune2fs -U 8144779b-ad38-4c1c-aa45-35065ad289e5 /dev/sda5
```

---

### Post by nmaster on 2010-07-14
EDIT: i was beaten to it!

---

### Post by luvgirl12345 on 2010-07-14
> **neal.m.master said:**
> EDIT: i was beaten to it!

Haha NP mate... you wrote allot xD I am going to format the drive to ntfs (move the original contents to another PC) then try again ;)

---

### Post by nmaster on 2010-07-14
> **luvgirl12345 said:**
> Haha NP mate... you wrote allot xD I am going to format the drive to ntfs (move the original contents to another PC) then try again ;)

yeah i had to do that too a long while back! ntfs is good since for windows and linux.  i'm not sure about os X though...  in any case, FAT32 was a hassle since my external drive had a greater capacity than my internal one. i had to spread the files over two different machines. lol

---

### Post by luvgirl12345 on 2010-07-14
> **neal.m.master said:**
> yeah i had to do that too a long while back! ntfs is good since for windows and linux.  i'm not sure about os X though...  in any case, FAT32 was a hassle since my external drive had a greater capacity than my internal one. i had to spread the files over two different machines. lol

yeah... filesystems... my internal one has over 600gb and I dual booted windows before (thought I didnt need linux to have allot xD I was only testing a new OS at that time) now I changed my mind and deleted windows because I dont have time to play games anyways lol

edit: I will be gone for a while. will report back when the archiver is done.

edit: while it was archiving i looked at the tutorial from drs305 and noticed one line: unmount swap... I never thought swap had ANYTHING to do with it. I unmounted it and after that it was REALLY easy to resize the partition. Now i have a backup and learned something!!! Thanks guys!! GO UBUNTU!!! xD

---

