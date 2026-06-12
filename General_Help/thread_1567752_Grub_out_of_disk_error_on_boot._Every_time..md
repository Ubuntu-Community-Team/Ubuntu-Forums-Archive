---
title: "Grub out of disk error on boot. Every time."
date: 2010-09-04
forum: General Help
---

### Post by TheSqueak on 2010-09-04
**Edit: This is somewhat inaccurate, please see post #16 on page 2 for my actual situation**


I'm more than a little confused by this. A little while back I had to reinstall my machine because I had a hard disk failure and I replaced my primary drive.

Everything went perfectly smoothly, but then a couple of weeks after that when I rebooted, it dumped my into the grub rescue console

```
error: out of disk.
grub rescue>
```

So, I found a solution to the problem on these forums, rebooted perfectly fine, and thought everything was fine. Until the next time I rebooted, when it happened again. And now, every single time I reboot, I get the same issue.

I have to do the following, each and every time I want to reboot - and i'm at a loss to explain why grub is borking itself every time.

Boot off a live cd.
Open a konsole window

```
sudo su -
mount /dev/sda6 /mnt
mount /dev/sda1 /mnt/boot
mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
chroot /mnt
grub-install /dev/sda
update-grub2
```

And then I ```
sudo reboot
``` from a non chroot'ed terminal window, and the machine boots fine.

Has anyone else seen this?


(Running Kubuntu Lucid)

---

### Post by rnerwein on 2010-09-04
hi
it's only a feeling but i think you get a problem with the UUID.
try : blkid -c /dev/null  
and have a look at your /etc/fstab if your UUID is correct.
ciao

---

### Post by TheSqueak on 2010-09-04
I've checked, and the UUID's reported from blkid -c match those in my fstab

---

### Post by TheSqueak on 2010-09-05
Nobody else has any clue?

---

### Post by garvinrick4 on 2010-09-05
Lets see what these codes says:
```
sudo fdisk -l
``` (lower case L)
```
sudo blkid
```  (lower case L second letter)

---

### Post by drs305 on 2010-09-05
Is this a dual-boot system and does it only happen after you have used Windows between Ubuntu starts?

I've seen posts about Windows (perhaps Win7) rewriting sections of the MBR or otherwise changing things back the way it wants them. I don't use Windows so I didn't pay much attention, but you might want to do a forum search using terms that might track down posts on that possibility.

---

### Post by TheSqueak on 2010-09-05
```
james@MuadDib:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00038fa9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         608     4881408   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             608      121602   971878401    5  Extended
/dev/sda5             608        1824     9764864   82  Linux swap / Solaris
/dev/sda6            1824       44376   341795840   83  Linux
/dev/sda7           44376      121602   620315648   83  Linux

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000561fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001   fd  Linux RAID autodetect

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ed420

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      182401  1465136001   fd  Linux RAID autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/md0: 1500.3 GB, 1500299125760 bytes
2 heads, 4 sectors/track, 366283966 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
```

and

```
james@MuadDib:~$ sudo blkid
/dev/sda1: UUID="c6dfd3a8-67d2-456b-bda4-f7f6c0d12c34" TYPE="ext4" 
/dev/sda5: UUID="ba712b14-d321-483b-8486-a0d2785bb0d0" TYPE="swap" 
/dev/sda6: UUID="9a848c7b-c783-4bc7-a1c8-d34f39fd8c2a" TYPE="ext4" 
/dev/sda7: UUID="4fc1f5b1-7774-4885-b47b-4fafa7c90df4" TYPE="ext4" 
/dev/sdb1: UUID="780611ab-5ab4-fd5a-4cb9-02ceb8758ec7" LABEL=":BigRaid" TYPE="linux_raid_member" 
/dev/sdd1: UUID="780611ab-5ab4-fd5a-4cb9-02ceb8758ec7" LABEL=":BigRaid" TYPE="linux_raid_member" 
/dev/md0: LABEL="LargeMirror" UUID="351c7081-91b5-453d-9f2f-8cdc4ff06548" TYPE="ext4"
```


And no, it's a single boot system, this PC has never had Windows on it

---

### Post by garvinrick4 on 2010-09-05
Well you are using "raid" do not know anything about "raid" config
Anyway if you want to try I can give you the way that works to install grub.
I find it simpler to label my partitions for mounting purposes when multiple partitions.
So put your Live CD in and boot her up.
open gparted and label your /boot sda1 lets say as boot. Right click on it and label it then hit apply arrow.
right click on sda6 your install and lets say label it lucid, apply it.
```
sudo mkdir /media/boot
``````
sudo mkdir /media/lucid
``````
sudo mount /dev/sda1 /media/boot
``````
sudo mount /dev/sda6 /media/lucid
``````
sudo grub-install --recheck --root-directory=/media/lucid /dev/sda
``````
sudo umount /media/boot
``````
sudo umount /media/lucid
```Boot into Linux install on HDD and
```
sudo update-grub
``````
sudo grub-mkconfig
```That should do her.

---

### Post by TheSqueak on 2010-09-06
I tried all of that, and when I went to reboot again, I got exactly the same problem :(

---

### Post by john newbuntu on 2010-09-06
Once you successfully boot into Ubuntu using the procedure you described, one more time run:
```
sudo update-grub
sudo grub-install /dev/sda
```Reboot and see if it helps.

If it does not work, post the output after running the script in: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by TheSqueak on 2010-09-06
I'm at work at the moment, i'll give it a shot later today.

Thanks for the help folks.

---

### Post by QLee on 2010-09-06
I wonder what happened to sdc, and why doesn't it have a valid partition table?

---

### Post by TheSqueak on 2010-09-06
> **QLee said:**
> I wonder what happened to sdc, and why doesn't it have a valid partition table?

sdc is fine, I just haven't created a partition table on it yet because i'm saving it for when I start running out of space on my other disks

---

### Post by TheSqueak on 2010-09-06
> **john newbuntu said:**
> Once you successfully boot into Ubuntu using the procedure you described, one more time run:
```
sudo update-grub
sudo grub-install /dev/sda
```Reboot and see if it helps.

The commands all returned fine with no error, but when I rebooted I had the same issue, and had to go through the liveCD process again.

One thing that I didn't mention before, because i'd forgotten, is that when I run the "update-grub2" command at the end of my long reboot process, I get a "cannot find list of partitions" error, but it reboots fine.



> If it does not work, post the output after running the script in: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Results attached

---

### Post by john newbuntu on 2010-09-07
Try the "Solution" part that meierfra has posted:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)

Now if you do not find the line in the 10_linux file, try it in this file and comment(add #) the suspect line:
/etc/grub.d/00_header

Rerun "sudo update-grub" and "sudo grub-install /dev/sda".  Reboot.  
If it does not work, revert back to the original files that you modified.(remove # in front of 'if') and rerun the above 2 commands.

Also in order to see if you can write to the environment file, post the outputs of the commands:
```
sudo grub-editenv list
cat /boot/grub/grubenv
```

---

### Post by TheSqueak on 2010-09-12
Ok, now it gets weirder, and i've just realised that most of what I said in my first post was wrong.

In actual fact, the situation appears to be that I can reboot perfectly successfully, but I can't boot up from a cold start without getting the grub errors.

I don't even need to let my live CD boot all the way into the desktop environment, just long enough for me to ctrl-alt-F1 into a console and sudo reboot and then the PC will tell me to remove the CD and will boot straight into my main system alright.

I can reboot from the main system and it will come up OK, but if I actually poweroff and then try to boot ... "out of disk" every time.


(Oh, and apologies for my delay in replying to this, i've been away for a while)

---

### Post by alexpage on 2011-02-08
Did you ever figure out what the problem was?  I have the same issue - cold boot never works ("out of disk" error) but I just Ctrl-Alt-Del and it comes back up fine.

---

### Post by TheSqueak on 2011-02-08
I never did - I cold boot so rarely I could never be bothered to take the time and hassle that troubleshooting it properly would have been

---

### Post by oldfred on 2011-02-08
Do you have mixed PATA & SATA drives? Sometimes BIOS will report them differently. It often promotes the PATA drive to sda.

---

