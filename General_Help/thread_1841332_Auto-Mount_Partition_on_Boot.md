---
title: "Auto-Mount Partition on Boot"
date: 2011-09-09
forum: General Help
---

### Post by Zelda Hunter on 2011-09-09
My browser's home page is located on my Windows partition; and apparently, I have to manually open my Windows partiton to mount it. I searched on how to auto-mount on boot and everyone's problem had been solved by pysdm, so I tried that. 

I found only one partition on the list of partitions/drives: sda5. This is the linux-swap partition. My Windows partition is sda3.

Could someone tell me another way to mount Windows (sda3) on boot or solve my lack of partitions in pysdm?

---

### Post by Bodsda on 2011-09-09
> **Zelda Hunter said:**
> My browser's home page is located on my Windows partition; and apparently, I have to manually open my Windows partiton to mount it. I searched on how to auto-mount on boot and everyone's problem had been solved by pysdm, so I tried that. 
 
I found only one partition on the list of partitions/drives: sda5. This is the linux-swap partition. My Windows partition is sda3.
 
Could someone tell me another way to mount Windows (sda3) on boot or solve my lack of partitions in pysdm?
 
I have never heard of pysdm... If you want to auto-mount partitions, you can add an entry to the fstab file. Bodhi.Zazen has an excellent PDF detailing this.
 
[http://bodhizazen.net/Tutorials/Understandingfstab.pdf](http://bodhizazen.net/Tutorials/Understandingfstab.pdf)
 
Hope this helps,
Bodsda

---

### Post by nothingspecial on 2011-09-09
Make a directory called /media/windows then make a backup of your current /etc/fstab and add a line to it like this
```

UUID=34NuMB3rs-l33TeRs-blah    /media/windows     ntfs-3g       auto,users,uid=1000,gid=100,dmask=027,fmask=137,[COLOR="Red"]locale=en_GB.utf8[/COLOR]  0   0
```

Then test it with ```
sudo mount -a
```

find /dev/sda5's UUID by typing ```
sudo blkid
```

and use your locale

**EDIT** or read bodhizazens guide as linked above

---

### Post by Morbius1 on 2011-09-09
The Jedi way.

First: If you currently have the partition mounted unmount it.

[1] Run the following command to find all your partitions:
```
sudo blkid -c /dev/null
```Among the list should be your Windows partition and it might look something like this:
> /dev/sda3: LABEL="WinXP" UUID="DA9056C19056A3B3" TYPE="ntfs" [2] Create a permanent home for the partition to line in:
```
sudo mkdir /media/Windows
```[I][COLOR=Blue]Note: If you create a mount point in your home directory or in /media it will place a mount icon on your desktop. If you don't want that to happen create a mountpoint somewhere else like /mnt/Windows or even /Windows.[/COLOR]

[/I][3] Edit fstab as root:
```
gksu gedit /etc/fstab
```[4] Add the following line to the end of fstab:
```
UUID=DA9056C19056A3B3 /media/Windows ntfs defaults,nls=utf8,uid=1000,umask=000 0 0
```[COLOR=Blue]*The UUID number will be different for your setup.*[/COLOR]

[5] Save fstab, exit gedit, and run the following command to test for errors and mount the new partition:
```
sudo mount -a
```

---

### Post by Zelda Hunter on 2011-09-09
That worked. all of you practically had the same answer, and they all worked... simultaneously. :P

Thanks!

---

