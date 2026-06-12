---
title: "Terminal Problem"
date: 2010-06-16
forum: General Help
---

### Post by rcline112 on 2010-06-16
I'm dual-booting Ubuntu with Windows XP. I've been using this setup for over 18 months now. This problem first occurred around one week ago.

When I open a terminal window in Ubuntu 9.10, the window opens with a blinking cursor and no prompt. When I try inputting anything, nothing appears and my computer freezes; this usually requires a reboot. I tried opening the window without trying to input anything. The cursor blinked, and I waited. Ninety seconds later, the window auto-closed with no message. I was able to continue using anything else but the prompt.

*Potentially unrelated: I've recently not been able to use Google Chrome. Mozilla Firefox works fine. When clicking the icon or selecting in a menu, it acts as if it will open, but nothing every appears--not even a window.*

Nonetheless, I'm curious to find out if there is a solution for this terminal issue. I'd like to know if there are any diagnostic tools that might give some perspective on the situation too.

---

### Post by Smart Viking on 2010-06-16
What happens if you press "ctrl+alt+f2"? (Press alt+f7 to get back to the desktop) If there is a terminal there, and it works, then your problem might have something to do with "gnome-terminal".

If that was true, go to ubuntu software center and search for "terminal", and then install one of the alternatives to "gnome-terminal".

I hope this helped a little. :)

---

### Post by MooPi on 2010-06-16
Try this to see if it is gnome-terminal issue or a terminal issue. ```
Alt + F2
```
```
xterm
```
This can function as an alternate and test.
I would then see if maybe an update didn't complete
```
sudo dpkg --configure -a
```

---

### Post by rcline112 on 2010-06-16
When I use Ctrl+Alt+F2, it proceeds to a full screen terminal with a login prompt. I input my  login information and the it accepts and begins displaying information similar to that when logging in normally. A few seconds later, messages seeming to be errors begin appearing scrolling slowly on the screen.

It follows a basic pattern that constantly repeats for a couple minutes. The following is the last section of the cycle (where Triton is the computer name):
```

...
[ 2334.128709] ata1.00: status: { DRDY ERR }
[ 2334.128754] ata1.00: error: { UNC }
[ 2337.830019] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2337.830078] ata1.00: BMDA stat 0x24
[ 2337.830136] ata1.00: cmd c8/00:08:d2:8c:f3/00:00:00:00:00/e6 tag 0 dma 4096 in
[ 2337.830139]          res 51/40:05:d5:8c:f3/40:00:06:00:00/e6 Emask 0x9 (media error)
[ 2337.830242] ata1.00: status: { DRDY ERR }
[ 2337.830287] ata1.00: error: { UNC }
[ 2337.852995] end_request: I/O error, dev sda, sector 116624597
Ubuntu 9.10 Triton tty2

Triton login:

```
After this last repeat, it prompts for a login again as shown above. There is never an opportunity to input commands at a prompt, before or after logging in.

The keystrokes Alt+F8 did not return me to my Ubuntu desktop, but I accidentally discovered that Alt+F7 does.

Maybe this output enhances the cause of the problem, but currently I'm still unable to use even this full screen terminal to input commands.

---

### Post by MooPi on 2010-06-17
From the info you posted it may be a hard drive issue. If you boot from the live CD and open a terminal there you can attempt to fix the hard drive.
 From the terminal under the Live CD ```
sudo fdisk -l
```From this command it should list all partitions on your hard drive . It will look something like this:
   ```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1480       19457   144408285   83  Linux
/dev/sda2            1415        1479      522112+  82  Linux swap / Solaris
/dev/sda3   *           1        1414    11357923+  83  Linux

```My boot partition is sda3 marked by the asterisk so ignore that.
From this output you can select the partition that is your boot partition probably sda1.
Now use ```
e2fsck -f -n /dev/sda1
``` This command will force check your drive but not make any changes. If the check comes back with errors ```
e2fsck -p /dev/sda1
```This command will attempt automatic repair of the drive.

---

### Post by rcline112 on 2010-11-10
I ran the following as suggested:

```
sudo fdisk -l
```

Below is the output I received:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6515    52331706    7  HPFS/NTFS
/dev/sda2            6516        9729    25816455    5  Extended
/dev/sda5            6516        9590    24699906   83  Linux
/dev/sda6            9591        9729     1116486   82  Linux swap / Solaris

```

As mentioned previously, I dual boot using GRUB. Is the partition that I need to run the other commands you listed earlier, MooPi, going to be /dev/sda1? The reason I ask is because when I run
```
sudo e2fsck -f -n /dev/sda1
```
I receive the following output:
```
ubuntu@ubuntu:~$ sudo e2fsck -f -n /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

---

### Post by dcstar on 2010-11-10
> **rcline112 said:**
> 
........
```
sudo e2fsck -f -n /dev/sda1
```
I receive the following output:
[CODE]ubuntu@ubuntu:~$ sudo e2fsck -f -n /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda1
.......

Do **not **run EXT2 commands on NTFS partitions.

---

