---
title: "from bad to worse......"
date: 2011-03-03
forum: General Help
---

### Post by macd0g on 2011-03-03
so, i posted a few days ago that i wanted my second hdd to mount automatically. 
i found a program called ntfs-config and installed it.

it didnt work.

when i restarted the computer it would come up with not found or something like that, in the startup/splash screen, so i have to push "S" to skip.

so, i figured the bootup needed a longer time to recognize the hdd was there, so i installed startup manager and set the 10 second timeout to 20 seconds, thinking this would be enough time for the hdd to become recognized.

it didnt work.

it now doesnt recognize my secondary hdd AND my external usb drive.
i tried removing and purging both programs, but it hasnt helped.  i tried re-installing the programs and returned everything to how it was, but this doesnt seem to have worked either.  
i CAN see the hdd's but the usb no longer mounts automatically, and the second internal hdd is how it was before, but i have to wait to push "S" on every startup.
any ideas?  system restore in ubuntu tweaks doesnt work :(


ok, i just tried double clicking on my 2nd hdd (the important one with all my stuff on it), and it came up with this

Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdg1 on /media/New_Volume

aaargh!, what does this mean?  how do i fix it?


pleeeease!!!!

---

### Post by Grenage on 2011-03-03
Could you please post your /etc/fstab file, and the results of:

```
sudo fdisk -l
```

---

### Post by coffeecat on 2011-03-03
Hi.

ntfs-config was a good idea when it was first developed but it hasn't been maintained since and is best avoided. I'm glad you've uninstalled it. In order to see what it's done wrong, and what deeds to be done to correct it, we'll need the output of some terminal commands. First, though, open a 'Computer' file browser window (Places menu) and navigate to 'Filesystem' > /etc folder. Look for the file called 'fstab' in the /etc folder and double-click on it. It will open read-only in a text editor. Copy and paste the contents of /etc/fstab and post it here.

Now open a terminal (Applications > Accessories) and post the output of these three commands. To copy and paste, highlight the output that needs copying, then right-click and 'Copy'.

```
sudo blkid
sudo fdisk -lu
ls -l /media
```Please post all the output and the contents of /etc/fstab between [noparse]```
 and 
```[/noparse] tags for legibility. You can use the # icon in the message toolbar for this if you wish.

---

### Post by macd0g on 2011-03-03
haha!! is it that obvious that i havent got a clue what i am doing.  i appreciate the step by step instructions :)

fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sda1	/	ext4	errors=remount-ro,user_xattr	0	1
/dev/sdg1	/media/New_Volume	ntfs	defaults,nls=utf8,umask=0222	0	0
/dev/sdb1	/media/external\040hdd	ntfs-3g	defaults,nosuid,nodev,locale=en_NZ.UTF-8	0	0
/dev/sdb2	/media/ubuntuee	ntfs-3g	defaults,nosuid,nodev,locale=en_NZ.UTF-8	0	0
/dev/sdc1	/media/New_Volume	ntfs-3g	defaults,locale=en_NZ.UTF-8	0	0
/dev/sda5	none	swap	sw	0	0

```

sudo blkid

```

monkey@monkey:~$ sudo blkid
/dev/sda: LABEL="ubunutee" UUID="2235efcd-b458-44f3-9d50-5d38c2035ccf" TYPE="ext4" 
/dev/sdb1: UUID="bd9c17c2-1b4d-4385-8153-4c2eebf21c68" TYPE="ext4" 
/dev/sdb5: UUID="6cc8ad85-2a96-4791-9b97-e6b514e0362b" TYPE="swap" 
/dev/sdg1: LABEL="New Volume" UUID="325C89EB5C89AA65" TYPE="ntfs"

```

sudo fdisk -lu
```

monkey@monkey:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006d650

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   150159359    75078656   83  Linux
/dev/sdb2       150161406   156301311     3069953    5  Extended
/dev/sdb5       150161408   156301311     3069952   82  Linux swap / Solaris

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3baafbfc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1            2048   976769023   488383488    7  HPFS/NTFS
monkey@monkey:~$ 

```


ls -l /media
```


monkey@monkey:~$ ls -l /media
total 180
drwxr-xr-x 2 root   root     4096 2011-03-03 22:31 drive
drwxr-xr-x 2 root   root     4096 2011-03-03 21:27 external hdd
drwxr-xr-x 2 root   root     4096 2011-03-03 20:48 New_Volume
drwxrwxrwx 1 root   root   163840 2011-03-02 16:53 sdg1
drwxr-xr-x 2 root   root     4096 2011-03-03 21:27 ubuntuee
drwx------ 3 monkey monkey   4096 2011-03-03 22:21 ubunutee
monkey@monkey:~$ 

```
btw, the "sdg1" in line 5 of the last output was highlighted....

thanks for the quick responses.

---

### Post by coffeecat on 2011-03-03
There's something very odd going on. ntfs-config has made a mess of things (nothing new there then!) but there are other factors.

First - your sda drive has an ext4 filesystem in the raw drive without any partitions. Possible but unusual. How did you create that?

Second, the entries for sdb1 and sdb2 in fstab (presumably created by ntfs-config) are for ntfs partitions, but sdb1 and sdb2 are (primary) ext4 and extended partitions respectively. Have you changed the drive connectors around, or changed the boot order in the BIOS?

There are fstab entries for both sdc1 (which is non-existent) and sdg1 mounting to the same mountpoint. I've see a thread before where ntfs-config has done this. Have you any idea what sdc1 might have been?

Lastly - do you really need a fstab entry for your sdg 500GB drive? I presume that's the external USB one. Normally, if you plug it in it will automount, or if you plug it in and switch it on before you boot up, it will be automounted for you by the time you get to the desktop.

---

### Post by YesWeCan on 2011-03-03
As coffeecat says your fstab is pretty messed up. Try this instead:
```
# /etc/fstab: static file system information.
#
# <file system>                             <mount point>            <type>       <options>                          <dump>  <pass>
   
proc	                                    /proc	              proc	nodev,noexec,nosuid	                0	0
UUID=bd9c17c2-1b4d-4385-8153-4c2eebf21c68   /	                      ext4	errors=remount-ro,user_xattr	        0	1
UUID=6cc8ad85-2a96-4791-9b97-e6b514e0362b   none	              swap	sw	                                0	0

UUID=325C89EB5C89AA65	                    /media/New_Volume	      ntfs	defaults,nls=utf8,umask=0222	        0	0
```

---

### Post by macd0g on 2011-03-03
wow, thank you guys so much.  you made it such an easy thing to fix.  i made a copy my fstab (just to be safe), then pasted yeswecan's code.
it worked a treat.  it even auto mounted my 500gb hdd, which is what i was TRYING to do in the first place

thanks
:)

---

### Post by YesWeCan on 2011-03-03
Result! :)
Don't forget to mark this thread as "solved" using the Thread Tools menu above.

---

