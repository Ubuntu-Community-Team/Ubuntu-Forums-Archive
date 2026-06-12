---
title: "Vista keeps deleting my Linux partition"
date: 2009-09-28
forum: General Help
---

### Post by Havoc805 on 2009-09-28
I just  started  learning linux, and decided to duel boot it with windows vista.  Everything apeared to be fine until i noticed that bot OS's could see the entire harddrive.  I basically figured out that vista upon loading must have deleted the partition. Anyone know how to fix this?
I am gonna guess it has something to do with the ways the file structures are, / istead of c\.

Has anyone elese encountered this, or have a link to a similar post?


And deleting the vista partition isnt a option lol. DX10 has us all.....

---

### Post by DeMus on 2009-09-28
> **Havoc805 said:**
> I just  started  learning linux, and decided to duel boot it with windows vista.  Everything apeared to be fine until i noticed that bot OS's could see the entire harddrive.  I basically figured out that vista upon loading must have deleted the partition. Anyone know how to fix this?
I am gonna guess it has something to do with the ways the file structures are, / istead of c\.

Has anyone elese encountered this, or have a link to a similar post?


And deleting the vista partition isnt a option lol. DX10 has us all.....

Install Vista on a partition which is about half the size of your disk.
Then install Ubuntu on the other half.
During installation of Ubuntu choose to place Grub on the MBR (Master Boot Record). Grub will show you a list of available OS'es (Ubuntu and Vista).

---

### Post by Havoc805 on 2009-09-28
> **DeMus said:**
> Install Vista on a partition which is about half the size of your disk.
Then install Ubuntu on the other half.
During installation of Ubuntu choose to place Grub on the MBR (Master Boot Record). Grub will show you a list of available OS'es (Ubuntu and Vista).


I got the installs both up, its jsut now the entire drive is in Vista format(nts..w/e its called) so i cant save anything on linux. Bootloader still sees both versions. I installed Vista first and made the partiton in vista. After installing ubuntu and reloading windows windows did a checkdisk and realocated it.

EDIT: ty for the quick response

---

### Post by DeMus on 2009-09-28
> **Havoc805 said:**
> I got the installs both up, its jsut now the entire drive is in Vista format(nts..w/e its called) so i cant save anything on linux. Bootloader still sees both versions. I installed Vista first and made the partiton in vista. After installing ubuntu and reloading windows windows did a checkdisk and realocated it.

EDIT: ty for the quick response

How did you install Vista? Do you have a Vista disk or some recovery disk from a PC manufacturer?
How did you install Ubuntu? From the live CD or did you use Wubi?
When in Ubuntu, or if that doesn't work, start the live CD, open a terminal and type (one instruction at a time):
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

Place the output here please.

---

### Post by Havoc805 on 2009-09-29
Sorry with the late reply ( i crashed my cmos trying to use asus easy flash hint: dont do it through windows)


And thank you for the reply. 

Code:
Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36156   290422046    7  HPFS/NTFS
/dev/sda2           36157       36481     2610562+   5  Extended
/dev/sda5           36157       36459     2433816   83  Linux
/dev/sda6           36460       36481      176683+  82  Linux swap / Solaris
havoc805@havoc805-desktop:~$ sudo blkid
/dev/sda1: UUID="5EA0D986A0D964D5" TYPE="ntfs" 
/dev/sda5: UUID="50f646e3-2ac4-48eb-80ae-c6cfffc331e9" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="5ee3c231-3a98-45a6-937c-2cca16a602db" 
havoc805@havoc805-desktop:~$ cat /etc/ftstab
cat: /etc/ftstab: No such file or directory
havoc805@havoc805-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G   26M  99% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  104K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  152K  1.5G   1% /dev
tmpfs                 1.5G  476K  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sr0              504M  504M     0 100% /media/cdrom0
havoc805@havoc805-desktop:~$ 


I have to go but i am activly scanning this forum on the go. Like i said sorry for the late reply, got in over my head.

EDIT: when i ran  cat /etc/ftsab i got this....
Code:
havoc805@havoc805-desktop:~$ cat /etc/ftstab
cat: /etc/ftstab: No such file or directory

---

### Post by Vaphell on 2009-09-29
typo: fstab not ftstab

hint - when working with paths use [tab] key, it autocompletes (1x) or shows all valid options (2x). It helps to avoid typos
for example
**cat /e[tab]**(it finishes etc, because it's the only thing starting with e)**/f[tab][tab]**(shows all items starting with f)

---

### Post by Havoc805 on 2009-09-29
> **Vaphell said:**
> typo: fstab not ftstab

hint - when working with paths use [tab] key, it autocompletes (1x) or shows all valid options (2x). It helps to avoid typos
for example
**cat /e[tab]**(it finishes etc, because it's the only thing starting with e)**/f[tab][tab]**(shows all items starting with f)
 Thanks, after i left i fugured it was a typo i was in kind of a hurry :p Anyways ty for the Tab tip. Thats awsome.

her is what i got...

Code:
havoc805@havoc805-desktop:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=50f646e3-2ac4-48eb-80ae-c6cfffc331e9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5ee3c231-3a98-45a6-937c-2cca16a602db none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
havoc805@havoc805-desktop:~$ 


TY for the reply.

---

### Post by DeMus on 2009-09-29
> I got the installs both up, its jsut now the entire drive is in Vista format(nts..w/e its called) so i cant save anything on linux. Bootloader still sees both versions. I installed Vista first and made the partiton in vista. After installing ubuntu and reloading windows windows did a checkdisk and realocated it.


The entire drive is in NTFS format? But your output of the codes I gave you say different:

> Device Boot Start End Blocks Id System
/dev/sda1 * 1 36156 290422046 7 HPFS/NTFS
/dev/sda2 36157 36481 2610562+ 5 Extended
/dev/sda5 36157 36459 2433816 83 Linux
/dev/sda6 36460 36481 176683+ 82 Linux swap / Solaris

Although I must say that compared to the NTFS partition the Linux partitions are very small.

You don't mind installing again? Tou don't have valuable data on your disk yet? Okay, do this please:

[LIST=1]
[*]Boot from your Ubuntu disk and pretend you will install.
[*]Just go ahead until step 4 where you have to say how and where you want to install it. Choose to delete all partitions, do that one by one. Information on screen will tell you how to do that. After deleting the partitions stop the installation of Ubuntu.

[*]Boot from your Vista disk. One of the first questions you need to answer during installation is where you want to install Vista. Make a new partition with a size of 50GB (50.000MB) and install it there. Leave the rest open as free disk space.
[*]After installation enter Vista and make a D drive with a size of 100GB. Leave the rest of the disk free.

[*]Then boot from the Ubuntu disk and install. In step 4 you choose Manual.
[*]Make a partition for / (root) of 50GB, one for swap (2 times your ram size when it is max 1GB, 1 time your ram size when 1 - 2GB ram, and above that don't make a swap partition), and the rest of the disk should become the /home partition.
[*]Continue installation and at the end choose to place Grub in the MBR of your disk, to overwrite the Vista bootloader.
[/LIST]
This should give you a nice installation. Good luck. When you have questions or problems just write again, also when it's working write again please.

---

### Post by Havoc805 on 2009-09-29
Gonna try that right now.  Will post results.

---

### Post by QIII on 2009-09-29
Careful of language conventions with regard to decimals in large numbers, DeMus  (Mir war's klar ...)

To most native English speakers (particularly the States and much of the UK), 50.000 is "Fifty and Zero One thousandths", not "Fifty Thousand".  "Fifty Thousand" is rendered 50,000.

When I don't know the nationality of a poster, I punt.

---

### Post by admelfo on 2009-09-29
*Bad* Vista!

---

### Post by QIII on 2009-09-29
**[B] 	 Evil, wicked, bad, naughty Vista! You must spank her. **[/B]

---

### Post by DeMus on 2009-09-29
> **QIII said:**
> Careful of language conventions with regard to decimals in large numbers, DeMus  (Mir war's klar ...)

To most native English speakers (particularly the States and much of the UK), 50.000 is "Fifty and Zero One thousandths", not "Fifty Thousand".  "Fifty Thousand" is rendered 50,000.

When I don't know the nationality of a poster, I punt.

Sorry, I should have written 50000 without any decimal character. I only wanted to say the OP has to write 50000 (M) instead of 50 (G).
My mistake, sorry.

I'll be of to work now, will be home in about 11 hours.

---

### Post by Megrimn on 2009-09-30
Have you checked the *SIZE* of the NTFS partition?  because windows WILL NOT display the linux partition.  if GRUB isn't coming up, then yeah, go ahead and reinstall.  

If grub does come up when you boot with the 9.04 boot option in addition to windows, there is no problem, and no need to panic.  If you want the linux partition to be displayed in windows, you need to download the Ext2 IFS driver.

---

### Post by QIII on 2009-09-30
> **DeMus said:**
> Sorry, I should have written 50000 without any decimal character. I only wanted to say the OP has to write 50000 (M) instead of 50 (G).
My mistake, sorry.

I'll be of to work now, will be home in about 11 hours.

Nah.  No mistake...

So many languages ...

---

