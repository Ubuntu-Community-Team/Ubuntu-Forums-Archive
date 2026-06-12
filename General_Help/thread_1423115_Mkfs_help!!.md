---
title: "Mkfs help!!"
date: 2010-03-06
forum: General Help
---

### Post by blobstah on 2010-03-06
I was running ubuntu as a live cd and I wanted to format my pen drive into an ext3 filesystem. I put in sudo mkfs /dev/sda1, but know im thinking that sda1 was my HDD!! I removed the cd from my computer, and it wont boot up into windows anymore!!! The only thing that is giving me hope is that the mkfs took about 1 min to format whatever it was formatting (my pen drive or my hdd!!) and my hdd is 500gb big. Is there anyway that I could have accidentaly formatted my HDD? IF YES THAN PLZ HELP, somehow...!!

---

### Post by muteXe on 2010-03-06
pop in the live CD again, and when booted, from a terminal do "sudo fdisk -l" (that's a small "L", not a 1).

edit: and paste the results in here :)

---

### Post by ajgreeny on 2010-03-06
Yes, I'm afraid from your description that you did format your hard drive, and I think the **fdisk -l **command will show that your **ntfs** has now gone.

**DO NOT PANIC**

Whatever you do, make sure it is all done with a live CD from now, though it sounds as if it will all have to be, as you're unable to boot from the hard disk.  Judging by the short time it took to carry out the mkfs, it must have been a quick format, possibly just removing the partition table and replacing it, so you ought to be able to get it back.

Download a copy of TestDisk from [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) and use that to undelete your partition(s) and with luck you can get everything back as it was.

---

### Post by blobstah on 2010-03-06
The output of fdisk -l is:
/dev/sda1 hpfs/ntfs, so the ntfs was not delete? maybe I only deleted the boot sector of windows???
PLZ HELP!!
EDIT: it says that sda1 is a fat32, but a (subpartition?) of it is in ntfs.........

---

### Post by nothingspecial on 2010-03-06
Can you access the windows file system from the live cd?

---

### Post by blobstah on 2010-03-06
How can I do that, plz help, im really freaking out over here....

---

### Post by psusi on 2010-03-06
Yep, you formatted your windows partition.  You can for a try a hail mary with testdisk, but basically it's gone.

---

### Post by nothingspecial on 2010-03-06
> **psusi said:**
> Yep, you formatted your windows partition.  You can for a try a hail mary with testdisk, but basically it's gone.

Probably, but maybe not, as you said that was a pretty fast format.

[COLOR="Red"]**DO NOT USE YOUR COMPUTER FROM ANYTHING BUT THE LIVE CD. DO NOT SAVE ANYTHING TO IT IF YOU CAN ACCESS IT**[/COLOR]

Boot the live cd and try to mount your hard drive, it should be in the places menu.

If not go applications, terminal and type

```
sudo mkdir /media/windows
```

```
sudo mount -t ntfs /dev/sda1 /media/windows
```

if it tells you you have the wrong file system, try

```
sudo mount -t vfat /dev/sda1 /media/windows
```

Then browse to /media/windows to see if your stuff is still there

---

### Post by blobstah on 2010-03-06
nothin'.... does this mean that I am royally ******?

---

### Post by nothingspecial on 2010-03-06
Not necessarilly.

Have a look at testdisk

---

### Post by blobstah on 2010-03-06
I tried, but i dont really understand what or how you want me to do what I am supposed to do. I tried fixing my boot, but they said unable to fix and I did no find anything particularly helpful in their wiki... help!

---

### Post by blobstah on 2010-03-07
My computer is now giving me the message cannot boot form hard disk!!!

---

### Post by nothingspecial on 2010-03-07
I think you`ve probably toasted your windows but you should still be able to mount it from the live cd to check. Can you copy and paste the output of ```
sudo fdisk -l
``` from the live cd. You should be able to access the internet from it.

---

### Post by blobstah on 2010-03-07
I am using gparted live cd, so I have no browser, but the output says that both sda1 and sda3 are ntfs, and says that the pc should boot from sda1

---

### Post by nothingspecial on 2010-03-07
Help me help you.

Can you download and boot a linux live cd?

---

### Post by nothingspecial on 2010-03-07
Have you tried to mount those 2 partitons to see if the data is still there?

---

### Post by blobstah on 2010-03-07
I apologise for giving you so little info, its because im very nervous. Anyways I have tried to mount both these partitions and undelete them in test disk, they would not mount, and test disk said that they were corrupt...........

---

### Post by nothingspecial on 2010-03-07
If you have stuff you do not want to loose in those partitions then you need to wait for someone who knows more about recovery.

If you have backups (which you should have), then installing Ubuntu to your hard disk [COLOR="Red"]"may"[/COLOR] allow you to boot windows.

Again, you should be able to mount your hard disk to the live cd.

---

