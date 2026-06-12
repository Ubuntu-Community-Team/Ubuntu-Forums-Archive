---
title: "Permanently mount external hard-drive"
date: 2010-03-17
forum: General Help
---

### Post by motorcity909 on 2010-03-17
Hi all

I've recently started using a 500gb external hard drive for music and backups.  It is always plugged into the computer but doesn't always mount at boot-up and I have to dis-connect and re-connect the USB cable.  The desktop icon then appears.

The fact that it's mount point changes also means I can't share the Music folder on the external hard drive via Samba (WinXP machines say they can't access the folder) and also Songbird 'loses' the tracks.

How do I permanently mount the external hard drive?  I assume it will mean some editing of the fstab file?  Unfortunately, I've got no idea of what I should enter on there.

The external hard drive volume is called 'Music and BackUps' - Gparted screengrab attached.

Any help is appreciated as always,
Dave

---

### Post by e1f on 2010-03-17
Hi,

If you manually mount your external drive then open a terminal and type: **df** you should see a line with your external drive device and it's mount point. 

eg: /dev/ad0s1a    1.9G    255M    1.5G    14%    /media/CEYEG363

You can then take that information and create a new entry in your fstab file.  First of all you want to create a mount point (sudo mkdir /external) and then open the fstab file (sudo nano -w /etc/fstab).

Add this to the bottom of the file:
**/dev/yourdevicehere!!             /external          ext3    rw              0       0**

You'll want to change the device to match the one you saw when you used the **df** command and make sure you use the correct filesystem, I've used ext3 in this example although your drive may use something different (ext4,fat32,ntfs).

After you've saved the file in nano you can manually mount the drive using your new fstab entry to ensure it works: 
sudo mount /external

If you get no errors from this command and you can see your files in /external everything worked fine and in the future this will be automatically mounted.

---

### Post by prodigy_ on 2010-03-17
A simple solution (according to the screenshot you posted).

1. Make a folder, called, for example /media/external: ```
sudo mkdir /media/external
```
2. Make yourself the owner of this folder: ```
sudo chown -R $(id -u):$(id -u) /media/external
```
3. Add a line to your /etc/fstab like the following: ```
/dev/sdb1 /media/external ntfs rw,nosuid,nodev,default_permissions 0 0
```


A more complicated, but also more correct way is to use ```
sudo blkid
``` command that outputs UUIDs for all partitions. Then in your fstab file you can refer to a partition by its unique ID. For example: ```
UUID=f1ff7651-b02f-4d05-907a-fe4990fd3d14 /media/external ntfs rw,nosuid,nodev,default_permissions 0 0
```

---

### Post by motorcity909 on 2010-03-19
Thanks both for your replies but I'm afraid I'm more confused than before.

The output from **df** is 

```
/dev/sdf1  488384032 106303400 382080632  22% /media/Music and BackUps
```When mounted the hard-drive appears in /media and I want to keep it's volume name of 'Music and BackUps', so I don't quite understand why I've got to create a new folder called /external.

But assuming I do that, is this the line to add to fstab -

**/dev/Music and BackUps/external          ntfs    rw               0       0**

Apologies if I seem dumb but this all seems rather complicated just to keep an external hard drive connected.  I had to re-connect it again this morning.

Thanks for any help
Dave

---

### Post by Morbius1 on 2010-03-19
The correct syntax if you're going to use a label is different from what you've got.

***STEP 1: Create a mount point for your partition to live in***

Open **Terminal**
Type **sudo mkdir /media/external**


*** STEP 2: Alter the fstab entry from this:***
>  **/dev/Music and BackUps/external          ntfs    rw               0       0**To this:
```
LABEL=Music\040and\040BackUps /media/external ntfs defaults,nls=utf8,umask=000,uid=1000    0    0
```The "\040" is how linux handles spaces in this situation. Linux hates spaces.
umask=000 will allow everyone to read and write to that partition
uid=1000 will make you the owner. To make sure that's the right number for you type: **id** in a terminal.

I'm making you the owner so that you can use Nautilus-share to share the drive with others on your network.

***Step 3: Mount it***

Open **Terminal**
Type [B]sudo mount -a

[/B][COLOR=Blue]Note: In dealing with external drives it's best not to use /dev/sdxy. Should you remove the drive and insert another one it too will will be sdxy but this time it might be a FAT32 or ext3 formatted drive and your fstab entry would be wrong. Also, and this is a big one, that fstab entry I recommended will work only if the drive is on before you boot as you stated in your original post. [/COLOR]

---

### Post by motorcity909 on 2010-03-19
Thanks Morbius

I followed your steps - with the external hard-drive connected - I hope that was right.

It seems to have worked fine except the contents of the external hard-drive now show twice in the /media folder - once under the new 'External' folder I created and once as the original 'Music and BackUps' - screengrab attached.

(The hard-drive icon on my screen takes me to /media/Music and Backups)

Is this correct?  Is my data on the external hard-drive duplicated now?

Apologies again if these are dumb questions.

Many thanks
Dave

---

### Post by motorcity909 on 2010-03-19
Me again.

I think I've just answered my own question.

I copied a couple of files across in to the new media/external folder and they showed up when i opened the external hard-drive via the desktop icon.

I then did the same the other way round - copied them into folders opened via the desktop icon and the files were also there under media/external

So, the data obviously isn't duplicated.  

And I can continue to use the entries in my Places menu pointing to the 'MusicHD' and the 'BackupsHD' folders on the external hard-drive.

I assume the new **media/external** folder is merely a shortcut (for want of a better word) to the external hard-drive?

Dave

---

### Post by Morbius1 on 2010-03-19
Open **Terminal**
Type **sudo umount /media/"Music and Backups"**

If that doesn't work: **reboot**

If you still have multiple entries, post your fstab so we can see what needs to be deleted:

Open **Terminal**
Type [B]cat /etc/fstab

[COLOR=Blue]EDIT: In looking at your output just post the fstab. I think you have multiple entries in there for the same partition.

/media/external is not a shortcut. It is the mount point for the device.
[/COLOR] [/B]

---

### Post by motorcity909 on 2010-03-19
I ran the first command but it said it couldn't find 'Music and BackUps'.

I also noticed in System Monitor it was showing twice - see screengrab *system monitor1*

I therefore rebooted - the media/external folder is now showing as empty - see screengrab - *media - file browser*.

System Monitor just shows the external hard-drive once - see screengrab *system monitor2*

After reboot, I noticed your edit so here is the fsatb output

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda1 during installation
UUID=5e48d577-470d-458a-87a1-24a6ea9c7574 / ext3 relatime,errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=14e70801-261d-4e25-b8bd-b95575ba6509 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
LABEL=Music\040and\040BackUps /media/external ntfs defaults,nls=utf8,umask=000,uid=1000    0    0
```I've got a copy of the fstab prior to the changes so can always put that back if we need to.

Thanks
Dave

---

### Post by Morbius1 on 2010-03-19
Post the output of the following command and please don't mount anything else manually please:

[B]subo blkid -c /dev/null
[COLOR=Blue]
Correction: You're getting me flustered: it should be [/COLOR]sudo blkid -c /dev/null
[/B]

---

### Post by motorcity909 on 2010-03-19
Hi Morbius

Apologies for the confusion and flustering.

I haven't mounted anything manually - I simply rebooted and the external hard-drive was there on my desktop.

The output you wanted -
```

/dev/sda1: UUID="5e48d577-470d-458a-87a1-24a6ea9c7574" TYPE="ext3" 
/dev/sda5: UUID="14e70801-261d-4e25-b8bd-b95575ba6509" TYPE="swap" 
/dev/sdb1: UUID="58BC438ABC43619C" LABEL="Music and BackUps" TYPE="ntfs"
```

I really appreciate all your help
Dave

---

### Post by Morbius1 on 2010-03-19
When you run:

**sudo mount -a**

Does it give you an error message?

---

### Post by motorcity909 on 2010-03-19
Nothing happens.

It just goes back to **myname@myname-desktop:~$**

---

### Post by Morbius1 on 2010-03-19
And do you have /media/external back?

[COLOR=Blue]EDIT: If you do reboot and see if you have only one mount point - /media/external[/COLOR]

---

### Post by motorcity909 on 2010-03-19
Have rebooted.

media/external is still an empty folder.

media/Music and BackUps is also still there as is the desktop icon to the external hard-drive.

---

### Post by Morbius1 on 2010-03-19
Well, it looks like I'm about to be late for a meeting, sorry.

There's something odd about all this. If there was something wrong with the fstab entry "mount -a" should have given you an error. Since it's automounting itself sometimes it would appear that the fstab entry is being completely ignored. Sometimes the external drive is identified as sdb1 and other times as sdf1.

I have a theory - don't know how good a one it is. Is this external drive drawing power from the box or does it have it's own power supply?

It's possible that fstab is being executed before the drive is powered up. That would explain the fstab entry being ignored because it's happening before the drive is operational. It would then default to automount as ubuntu normally does. Do you have a separate power supply available for that drive so you can start the drive and then boot into the Ubuntu box?

---

### Post by motorcity909 on 2010-03-19
The external drive has it's own power supply and is left plugged into power even when computer is off.

I really appreciate your help with this - have a good meeting and maybe talk later.

Thanks
Dave

---

### Post by motorcity909 on 2010-03-21
Well, we must have done something right.

Since Friday, everytime I've re-booted the computer the external hard-drive has been automatically mounted (icon on the desktop). 

Furthermore, Songbird can still see all of the music from the external hard-drive, despite it sometimes showing as **dev/sdb1** and sometimes as **dev/sdf1** in System Monitor.

Meanwhile that folder we created (*media/external*) just shows as empty.

So, working on the motto that "if it ain't broke, don't fix it", I'm leaving it well alone now, very content with how it's working.

Cheers
Dave

---

