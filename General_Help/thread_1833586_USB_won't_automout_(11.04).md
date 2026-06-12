---
title: "USB won't automout (11.04)"
date: 2011-08-26
forum: General Help
---

### Post by liranvaknin on 2011-08-26
Hello guys,
Yesterday I installed ubuntu 11.04 on my machine after trying mint linux and not liking it.
But now I have this strange problem that none of the usb mass storage devices (my phone,card reader and such) that I connect to the system automount.

I checked gconf-editor under: apps>nautilus>prefrences>media_automount is checked

But still no automount... (By the way I manage to mount them manually)

Any idea guys?

---

### Post by raja.genupula on 2011-08-26
check this command 

```
lsusb
``` in terminal . its gonna let you know is it  properly connected or not ?

---

### Post by raja.genupula on 2011-08-26
if it is connected and still not opening then , get resolve with this 

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by liranvaknin on 2011-08-26
Already followed this:
**Configuring Automounting**

 To enable or disable automount open a terminal and type **gconf-editor** followed by the **[Enter]** key. 
Browse to **/apps/nautilus/preferences/media_automount**. 
The **media_automount**  key controls whether to automatically mount media. If set to true, then  Nautilus will automatically mount media such as user-visible hard disks  and removable media on start-up and media insertion. 
There is another key **/apps/nautilus/preferences/media_automount_open**.  This controls whether to automatically open a folder for automounted  media. This key can also be set in the Nautilus (file manager) window.  From the **Edit** menu in Nautilus select **Preferences** and then select the **Media** tab.  
If  set to true, then Nautilus will automatically open a folder when media  is automounted. This only applies to media where no known x-content/*  type was detected; for media where a known x-content type is detected,  the user configurable action will be taken instead. This can be  configured as shown below. 


But still it only mount manually.. :(

---

### Post by liranvaknin on 2011-08-26
I still can't manage to mount them automatically..
Any one?! :confused:

---

### Post by liranvaknin on 2011-08-26
I tried to ask some people on the irc channel but no luck there...
there is the dmesg output when I plug a disk on key:

[15713.268023] usb 1-10: new high speed USB device using ehci_hcd and address 24
[15713.401797] scsi27 : usb-storage 1-10:1.0
[15714.401727] scsi 27:0:0:0: Direct-Access     SanDisk  Cruzer Blade     1.00 PQ: 0 ANSI: 2
[15714.402407] sd 27:0:0:0: Attached scsi generic sg5 type 0
[15714.403726] sd 27:0:0:0: [sdd] 15625216 512-byte logical blocks: (8.00 GB/7.45 GiB)
[15714.407598] sd 27:0:0:0: [sdd] Write Protect is off
[15714.407603] sd 27:0:0:0: [sdd] Mode Sense: 03 00 00 00
[15714.407606] sd 27:0:0:0: [sdd] Assuming drive cache: write through
[15714.411577] sd 27:0:0:0: [sdd] Assuming drive cache: write through
[15714.415372]  sdd: sdd1
[15714.418605] sd 27:0:0:0: [sdd] Assuming drive cache: write through
[15714.418611] sd 27:0:0:0: [sdd] Attached SCSI removable disk


Is there any chance that the problem is that the usb device own by the root user when i plug it? (in this case sdd1)

ls -l /dev/sdd1
brw-rw---- 1 root disk 8, 49 2011-08-26 23:15 /dev/sdd1

---

### Post by garvinrick4 on 2011-08-26
Not applicable.

---

### Post by liranvaknin on 2011-08-26
The location:
/media
Is owned by the root user..

Inside /media there are:
sdb1
sdb2
sdc1
all owned by root too.
Which are my other hdd that are mounted by fstab.

---

### Post by garvinrick4 on 2011-08-26
Just to see what it says. Install ubuntu-tweak
I have just installed maybe a week or so ago and functions very well.
It does say you are mounted in:
cd /media
ls -la
You can change to owned by you anytime you desire:
sudo chown -R rick:rick /media/whatever label in /media

Do they mount in Nautilus?
You say in Nautilus but does not mount on desktop correct, give ubuntu-tweak ago just to see if it mounts on
desktop?

---

### Post by liranvaknin on 2011-08-26
ubuntu tweak won't help because the device is not even mounted so there is no way he will show on the desktop.
chown to /media/xxx won't help either because i don't know what name the system will give the device...
now it's sdd1 tomorrow it can be sde1 because sdd1 will be taken by other device like a card reader.

I considering a reinstall of the system... this is frustrating!

---

### Post by garvinrick4 on 2011-08-26
Will it mount by UUID in fstab.
# /dev/sda7
UUID=0f7c5de9-c3b4-4c50-b288-d34e9ef6e119 /media/home       ext4    defaults      0
# /dev/sda8
UUID=1927A02F2C3A884A /media/data   ntfs-3g  defaults,local=en_US.utf8 0 0

Above is one in ext4 and one in ntfs. Do not like mounting in sda# they can change
as you said.

Though I do not automount usb drives but never had a problem mounting one.

Does it show you UUID in
```
sudo blkid
``` (lower case L second letter)

---

### Post by liranvaknin on 2011-08-26
it does show me the uuid.
But again, I don't want to enter every device I have to fstab.. (this is not auto mounting)
I just want the system to mount it automatically... just like when in windows you plug card reader it mounts it automatically.
and i know this is possible in ubuntu because it worked for me before in another installation.

---

### Post by garvinrick4 on 2011-08-26
Does it show up in Disk Utility to give label.
then make directory and mount.
```
sudo mkdir /media/portable
```
```
sudo mount /dev/sdd1 /media/portable
```

Just trying to give you some options.

> ls -l /dev/sdd1
brw-rw---- 1 root disk 8, 49 2011-08-26 23:15 /dev/sdd1 	
Showed up in this post of yours.

Here is mine a usb drive.
rick@rick-laptop:~$ ls -l /dev/sdb1
brw-rw---- 1 root disk 8, 17 2011-08-26 13:22 /dev/sdb1

---

### Post by garvinrick4 on 2011-08-26
> **liranvaknin said:**
> it does show me the uuid.
But again, I don't want to enter every device I have to fstab.. (this is not auto mounting)
I just want the system to mount it automatically... just like when in windows you plug card reader it mounts it automatically.
and i know this is possible in ubuntu because it worked for me before in another installation.
Understand, it is bumped up to front of Forum with all our posts, I have never had
automount problems in a long time in Ubuntu. Is it just that one USB drive? 
Do flash drives auto mount? Good luck to you liranvaknin? I got one more thing I
am going to google.

---

### Post by garvinrick4 on 2011-08-26
> After some research it seems this is caused (weird, I know...) by  the BIOS "Legacy Floppy" setting being enabled (it seems it's related to  [this]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/539515")).  So to fix it, all I had to do is restart the computer and next to the  "Floppy" setting in the BIOS I selected "Disabled" instead of "Legacy  Floppy" - problem solved, as soon as Ubuntu booted, automount was  working again and my USB devices were showing up in Nautilus again.

Hopefully this will help those of you having the same issue as I did.

Found this looking around From Forum, good luck.

---

### Post by liranvaknin on 2011-08-26
The floppy thing doesn't work...
And its happening not only with my usb flash drive but also with my phone as mass storage and card readers.
Should I reinstall ubuntu?

---

### Post by garvinrick4 on 2011-08-26
I have never had your problem happen to me in 100's of installs of Ubuntu.
It will take 20 minutes or so to install and then do your set-up, If no other cure
I would give that a go, if it comes out ok then do not ever have to think of it again.
Gets frustrating I know so go ahead. Let us know what happens in fresh install.

---

### Post by liranvaknin on 2011-08-26
[SOLVED]
Im soo stupid!!!
It was right there all the time!!!
I was just about to do a full reinstall and I backed up my fstab and then open it to see that it really backed up... here is what I saw:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd2 during installation
UUID=cc87421d-3884-4611-9bc1-c6fd0cdad15f /               ext4    errors=remount-ro,user_xattr 0       1
/dev/sdd1       none            swap    sw              0       0
#500GB HDD
#52GB Partition
UUID=DE14C44714C4247D /media/sdb1    ntfs-3g    default    0    0
#448GB Partition
UUID=16DC8097DC807333 /media/sdb2    ntfs-3g    default    0    0
#160GB HDD
UUID=F20EC3C70EC382D9 /media/sdc1    ntfs-3g    default    0    0


So so simple and I still missed it...
changed the swap to the uuid of sda1 (which is of course the real swap device)
rebbot and there you go... i've got my auto mount again!

garvinrick4 thanks alot for all the help, I really appreciate it!

---

