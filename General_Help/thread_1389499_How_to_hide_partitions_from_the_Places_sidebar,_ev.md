---
title: "How to hide partitions from the Places sidebar, even if mounted"
date: 2010-01-24
forum: General Help
---

### Post by lifestream on 2010-01-24
> **[COLOR="DarkOrchid"]Please, please, don't tell me to read the man page or google it. I already did for the past 2-3 days >_<;[/COLOR]**

How do I...

    * Prevent the sdb1 + sdb2 ext4 partitions from being shown in Nautilus/Thunar Places sidebar.

    * Prevent the Western Digital SmartWare VirtualCD, sdr1, from being shown in Nautilus/Thunar Places sidebar. It is just a VCD that is part of the firmware of the external (sdb) hard drive. *GAG!*

I don't care if they are mounted or not, though I prefer if they aren't.
As long as they don't show up on the Places sidebar AT ALL, I'll be happy. I never use them, but keep mounting them by accident.


Here's my fstab, can you tell me why it's not doing the above?

```

# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc              proc    defaults                            0  0  
# Entry for /dev/sda3 :
UUID=0371cefa-d0d1-4580-87e1-4ac4f23fd3b0  /                  ext3    errors=remount-ro                   0  1  
# Entry for /dev/sda1 :
UUID=2cac15e9-c4ee-44cf-ace9-fcc7333c8b50  /boot              ext3    defaults                            0  2  
# Entry for /dev/sda4 :
UUID=38822f83-963c-4c1a-806b-8933cf8d8587  /home              ext3    defaults                            0  2  
# Entry for /dev/sda2 :
UUID=f49e33ca-0718-4be4-9980-822ebabe5850  none               swap    sw                                  0  0  
# I dont want to show these drives in Thunar
/dev/sdb1                                  /media/sdb1        ignore  defaults,locale=en_US.UTF-8         0  0  
/dev/sdb2                                  /media/sdb2        ignore  defaults,locale=en_US.UTF-8         0  0  
/dev/sdb3                                  /media/sdb3        ignore  defaults,locale=en_US.UTF-8         0  0  
# mount WD_BACKUP at boot
/dev/sdb4 /media/WD_BACKUP ntfs-3g auto,users,locale=en_US.utf8 0 0

```

---

### Post by Barriehie on 2010-01-24
The default action in the fstab file will automatically mount the devices at boot time.  I'm sure there is a good fstab tutorial in this forum but I've got [[color="blue"]this explanation[/color]](http://www.tuxfiles.org/linuxhelp/fstab.html) I discovered shortly after discovering linux.  Alternatively you could comment out the lines and then explicitly mount when needed.

Barrie

---

### Post by lifestream on 2010-01-24
> **Barriehie said:**
> The default action in the fstab file will automatically mount the devices at boot time.  
[s]
Hmm, the particular partition I'm interested in, is a NTFS-3g one, and I set it to autoboot, yet it won't.
```
/dev/sdb4 /media/WD_BACKUP ntfs-3g auto,users,locale=en_US.utf8 0 0
```
It does mount OK, but I have to do it manually. In other words, like I said, it is NOT mounting at boot. [/s](EDIT: Nevermind, it does work. I had posted an old copy-paste)

> Alternatively you could comment out the lines and then explicitly mount when needed.
Yes, however, the issue is, like I said, even if the partitions aren't mounted, they STILL show up in the Places sidebar. I don't want them to show up, ever, in the Places sidebar.



O______O !

---

### Post by Barriehie on 2010-01-24
> **lifestream said:**
> Hmm, the particular partition I'm interested in, is a NTFS-3g one, and I set it to autoboot, yet it won't.
```
/dev/sdb4 /media/WD_BACKUP ntfs-3g auto,users,locale=en_US.utf8 0 0
```
It does mount OK, but I have to do it manually. In other words, it is NOT mounting at boot.


Yes, however, the issue is, like I said, even if the partitions aren't mounted they sadly, still show up in the Places sidebar.



O______O !

Try adding an **rw** somewhere in there where you've got auto,user,**rw**,<rest of the line>

Hang on, I've just recently found the file on my machine where that data is stored.  It is............ :)  **~/.gtk-bookmarks** I think you can delete the lines for the items you don't want to display, or alternatively try to comment them out.  Whatever you do I'ld make a copy of the original file first.right off.

Barrie

---

### Post by lifestream on 2010-01-24
> **Barriehie said:**
> 
Hang on, I've just recently found the file on my machine where that data is stored.  It is............ :)  **~/.gtk-bookmarks** I think you can delete the lines for the items you don't want to display, or alternatively try to comment them out.  Whatever you do I'ld make a copy of the original file first.right off.

Barrie,  unfortunately, the .gtk-bokmarks does not specify which drives to show. It is just for user-added folder bookmarks.

The original file is blank, and your file-browser has the bookmarks it had when you first installed Ubuntu.

---

### Post by Barriehie on 2010-01-24
Check this out: [http://ubuntuforums.org/showthread.php?t=855523&highlight=hide+drives](http://ubuntuforums.org/showthread.php?t=855523&highlight=hide+drives)

---

### Post by lifestream on 2010-01-24
> **Barriehie said:**
> Check this out: [http://ubuntuforums.org/showthread.php?t=855523&highlight=hide+drives](http://ubuntuforums.org/showthread.php?t=855523&highlight=hide+drives)


Yes, I know I can remove the entries I do not want from fstab. 
That just causes them to unmount. 
I know how to unmount.


My problem is, **even if the partition is unmounted, I do not want it on the Places sidebar.** Currently, even if it is unmounted, partitions show up on the Places sidebar. **I don't want them there at all.**

I've done google search, I've done my homework, that's why I'm asking if anyone has been able to do this.

The best result I got from my search, was...
> **MoarningSun said:**
> 
The Windows partitions I wanted to hide were sda1 ans sda2, which initially didn't show in fstab. After I declared entries for the partitions in a specific manner the partitions were gone from the places menu!
```

# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=ac83da58-6e80-4602-bffa-9d6b4b30e34f / ext4 errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=013e3395-57a2-4c4d-92ea-663f02043a14 none swap sw 0
/dev/sda7 /media/DATA ntfs-3g defaults,locale=en_US.UTF-8 0 0

```in which sda7 is a mounted NTFS partition that I want to use with ubuntu, created it with 'ntfs-config'. I added two entries for ignoring the two partitions sda1 and sda2, with filesystem defined as 'ignore', so the /etc/fstab looked like this:

```

# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=ac83da58-6e80-4602-bffa-9d6b4b30e34f / ext4 errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=013e3395-57a2-4c4d-92ea-663f02043a14 none swap sw 0 0
/dev/sda1 /mnt/SDA1 ignore defaults,locale=en_US.UTF-8 0 0
/dev/sda2 /mnt/SDA2 ignore defaults,locale=en_US.UTF-8 0 0
/dev/sda7 /media/DATA ntfs-3g defaults,locale=en_US.UTF-8 0 0

```I'm not sure if the specified mount point or other options really matter and the directories /mnt/SDA1 and /mnt/SDA2 don't even exist.. but it seems to work this way. I think I did
```
sudo mount -a
```to update the places menu.

Please note that this is kind of an 'empirical' solution, not based on real knowledge. I found the ignore option in the fstab manual (type 'man fstab'  in terminal).

... but that's not working for me either.

---

### Post by lifestream on 2010-01-24
HA!
For the 4th time, I did what post 2 here says to do:
[http://ubuntuforums.org/showthread.php?p=8389479#post8389479](http://ubuntuforums.org/showthread.php?p=8389479#post8389479)
...
And it finally worked! My partitions are hidden! *bangs head*


So now, there's 1 thing left! The VCD (sdr1) still stays, even though I "ignored" it too:
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="block.device" string="/dev/sdb1">
      <merge key="info.ignore" type="bool">true</merge>
    </match>
  </device>
  <device>
    <match key="block.device" string="/dev/sdb2">
      <merge key="info.ignore" type="bool">true</merge>
    </match>
  </device>
  <device>
    <match key="block.device" string="/dev/sdb3">
      <merge key="info.ignore" type="bool">true</merge>
    </match>
  </device>
  <device>
    <match key="block.device" string="/dev/sr1">
      <merge key="info.ignore" type="bool">true</merge>
    </match>
  </device>
</deviceinfo>
```
So the original question...
How do I prevent the Western Digital SmartWare VirtualCD, sdr1, from being shown in Nautilus/Thunar Places sidebar. It is just a VCD that is part of the firmware of the external (sdb) hard drive. *GAG!*

---

### Post by jamesisin on 2010-01-24
You could reformat your external to eliminate that silly partition and remove the entry from fstab.  That's how I usually handle USB drives and such anyway.  (Be forewarned that sometimes you have to use Windows to remove some dumb-asped bs software the manufacturer has included for your bereavement.)

---

### Post by lifestream on 2010-01-24
> **jamesisin said:**
> You could reformat your external to eliminate that silly partition

Sadly, I can't. WD SmartWare if part of the MyPassport firmware, it isn't a partition. Not a hidden partition, even.
The firmware takes it upon itself to be annoying and force a virtualCD image to mount, and there's no way to remove it, on Windows, Mac, whatever.

See, even if I "eject" it, next time I open my file-browser, the VCD is there again!

> and remove the entry from fstab.
There is no entry, because it's a "virtual" CD; it's not a partition.

> that's how I usually handle USB drives and such anyway.
Lucky you. I'm steering away from WD USB drives from now on :P


[QUOTE=The Dumb People Who Made DumbWare]"The Virtual CD is the build into the firmware of the drive. There is no option to remove the virtual CD."[/QUOTE]
Amen. :(

---

### Post by jamesisin on 2010-01-24
I would do a little research.  I would but I'm on my way out at the moment.  I had to call the manufacturer of my thumb drive to get specific instructions (Windows only) to remove their bs.  I expect theirs was firmware too because gparted couldn't see/effect the alleged partition.  I suspect there is a solution; they have probably just made it a pain in the asp.

---

### Post by lifestream on 2010-01-25
> **jamesisin said:**
> I would do a little research.  I would but I'm on my way out at the moment.  I had to call the manufacturer of my thumb drive to get specific instructions (Windows only) to remove their bs.  I expect theirs was firmware too because gparted couldn't see/effect the alleged partition.  I suspect there is a solution; they have probably just made it a pain in the asp.

Oh, yes, they have instructions on how to hide the VCD on Windows and Mac, but not Linux.

But I know that the VCD "mounts" as /dev/sr1, so... there should be a way.. the method above, 

>   <device>
    <match key="block.device" string="/dev/sr1">
      <merge key="info.ignore" type="bool">true</merge>
    </match>
  </device>


Doesn't work as expected.
I figured, since it does block the other 2 partitions from being shown, that it would work for the VCD too.

Hmm..

---

### Post by jamesisin on 2010-01-25
If you have a Windows machine (or VM) you should be able to ditch the VCD using these instructions:

[http://www.wdc.com/wdproducts/updates/?family=wdsmartwareutilities](http://www.wdc.com/wdproducts/updates/?family=wdsmartwareutilities)

---

### Post by lifestream on 2010-01-25
> **jamesisin said:**
> If you have a Windows machine (or VM) you should be able to ditch the VCD using these instructions:

[http://www.wdc.com/wdproducts/updates/?family=wdsmartwareutilities](http://www.wdc.com/wdproducts/updates/?family=wdsmartwareutilities)

Well... yes, but that would only remove it on Windows. The VCD doesn't show on my Windows VM, even.
I need it off when I am using Ubuntu, which is 99.99% of the time I'm using a computer :P

But I finally found something that worked :)

[QUOTE=http://nixliving.blogspot.com/2010/01/enjoy-your-wd-my-book-1tb-drive-no-more.html]In fstab, add:
```
/dev/sr1 none udf rw,noauto 0 0
```[/QUOTE]

Gone. *poof!*

---

### Post by jamesisin on 2010-01-25
That page also included the solution you posted only the person used the UUID (which you should also in case the /dev designation changes).

> UUID=your_smartware_partitions_uuid_here none hfs rw,noauto 0 0

You can get your UUID here:

```
blkid
```

EDIT: Just noticed I neglected to give you both links above:

[http://superuser.com/questions/44318/how-do-i-remove-a-mybooks-wd-smartware-virtual-cd-from-my-desktop](http://superuser.com/questions/44318/how-do-i-remove-a-mybooks-wd-smartware-virtual-cd-from-my-desktop)

---

