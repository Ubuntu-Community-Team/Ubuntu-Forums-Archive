---
title: "BURG Installed Incorrectly - How to remove GRUB2 from Wrong Partition"
date: 2010-08-06
forum: General Help
---

### Post by Rendrago on 2010-08-06
I installed Ubuntu 10.04 via the alternate CD for Full Disk Encryption.

I wanted to alter the GRUB2 menu so I installed BURG after reading this thread:

[http://www.omgubuntu.co.uk/2010/07/burg-boot-loader-installation-themeing.html](http://www.omgubuntu.co.uk/2010/07/burg-boot-loader-installation-themeing.html)

Once I opened the BURG Manager Application I was prompted to install BURG and asked where to install it. The default is **SDA** which is BAD if you're running Full Disk Encryption. I did this. I SHOULD have chosen **/dev/mapper/computername-root** which is **/dev/sda1**.

So now I have a nice pretty BURG screen that doesn't take me to my unlock screen. To make matters worse, before I realized what I had done, I used the nice GUI to also Restore GRUB to **/dev/sda**.

I believe I need to remove GRUB2/BURG from **/dev/sda** and somehow get the MBR looking in the right place again.

I am able to choose, *“Ubuntu GNU/Linux ,with Linux 2.6.32-24-generic (recovery mode)”*. I then rather sloppily enter my passphrase, choose the boot normal option, enter my username & password, then **startx**.

I've been browsing the forums all day and can't seem to find someone with a similar screw up.

Any ideas on how to get rid of GRUB from **/dev/sda** and get the MBR looking at **/dev/sda1** again if that's _even my issue_!?

Here's sudo fdisk -l

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000180aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       60802   488135681    5  Extended
/dev/sda5              32       60802   488135680   83  Linux

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe8aaad72

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00090179

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   83  Linux

```

**HELP!**

Thank you.

---

### Post by spyrule on 2010-08-06
You might be able to go to the command line and type:

```
sudo grub
```Which should give you the GRUB boot prompt, which looks like this:

```
grub>
```Change to the correct disk and partition with:

```
root (hd0,0)
```hd0 being the first disk, and the 0 being the first partition on the first disk. If you want to point the GRUB to the first disk's second partition, you'd use:

```
root (hd0,1)
```For the third partition on the first disk, root (hd0,2); or, for the second disk's first partition you'd use: root (hd1,0), and so on. 

Once you've done the root command to the appropriate disk and partition, you can setup the GRUB with:

```
setup (hd0)
```That is, if you're on the first disk.

If you can point the grub to the right place and boot easily, then you might be able to backtrack to BURG's install and point it to the right place.

Let me know if that helps at all.

---

### Post by Rendrago on 2010-08-06
Thanks for the reply.

Looks like BURG did more than I thought. Even though I un-installed BURG, I'm still getting a BURG menu upon boot. I hit 'c' for the command line and it took me to 'grub>'. I tried root (hd0,0) but it says the partition does not exist. Tried 0,1 but I wasn't expecting that to work either. No setup command with BURG either I guess.

Since I was going for an ultra-clean install this time, I think I'll re-install again unless I get some more suggestions. Guess I should have done a backup before experimenting.

Thanks again for trying to help.

---

### Post by spiralx on 2010-08-07
I think all you can do in un-install burg, then re-install.  (I was able to use Synaptics Packet Manager).

You may want to re-install GRUB2 as well, as an interim measure, just in case you need to re-start your machine. The following worked for me ( I have a dual partition, Win-7 and Ubuntu):
[COLOR=blue]

Restore the MBR to Window's liking. You can use "mbr" or "lilo" to do  this. I prefer lilo. You use it to write to the MBR but don't actually  configure it. (You will see a message about needing to configure lilo -  don't).

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

That should make Windows happy.

Reinstall Grub 2. It shouldn't mess with what Windows sees:

sudo grub-install /dev/sda


Once everything is working you can remove lilo if you wish:
sudo apt-get purge lilo[/COLOR]

---

