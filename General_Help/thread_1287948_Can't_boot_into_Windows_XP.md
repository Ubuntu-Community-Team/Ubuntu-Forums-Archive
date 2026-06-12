---
title: "Can't boot into Windows XP"
date: 2009-10-10
forum: General Help
---

### Post by lainmaster on 2009-10-10
At least not from GRUB. I get "Error 12: invalid device requested"...

```
rootnoverify (hd0, 4)
savedefault
makeactive
chainloader +1
```Tried pressing "e" in GRUB to edit that, on the fly, and "b" to boot the changes. This is what I tried and got:

Tried:
```
rootnoverify (hd0, 1)
savedefault
makeactive
chainloader +1
```Got:
```
NTLDR is missing.
```Tried:
```
rootnoverify (hd0, 0 to 9 except 1)
 savedefault
 makeactive
 chainloader +1
```Got:
```
Error 12: invalid device requested
```The thing is, if I change my BIOS to boot from the CD, and put a CD that has some Windows files, Windows boots fine. While I'm inside Windows, I see Windows' drive as "D:\".

The files in that CD are:
```
boot.ini
WINNT.ini
WINXP.ini
BOOTCAT.bin
BOOTIMG.bin
ntdetect.com
ntldr
```This is the content of the boot.ini found in that CD:

```
[Boot Loader] 
timeout=30 
Default=multi(0)disk(0)rdisk(0)partition(1)\Windows 
 
[Operating Systems] 
multi(0)disk(0)rdisk(0)partition(1)\Windows="1ST TRY THIS seleccione esto primero" /fastdetect 
multi(0)disk(0)rdisk(1)partition(1)\Windows="2ND TRY THIS essayez ceci en deuzieme" /fastdetect 
multi(0)disk(0)rdisk(0)partition(2)\Windows="3RD TRY THIS wahlen Sie diesen Third" /fastdetect 
multi(0)disk(0)rdisk(1)partition(2)\Windows="4TH TRY THIS selezioni questo fourth" /fastdetect 
multi(0)disk(0)rdisk(0)partition(3)\Windows="5TH TRY THIS selecione este fifth" /fastdetect 
multi(0)disk(0)rdisk(1)partition(3)\Windows="6TH TRY THIS seleccione este sexto" /fastdetect 
multi(0)disk(0)rdisk(0)partition(4)\Windows="7TH TRY THIS essayez ceci en septieme" /fastdetect 
multi(0)disk(0)rdisk(1)partition(4)\Windows="8TH TRY THIS wahlen Sie dieses achte" /fastdetect 
C:\="9TH TRY THIS selezioni questo nono" 
D:\="10TH TRY THIS selecione este decimo"
```With multi(0)disk(0)rdisk(0)partition(2)\Windows="3RD TRY THIS wahlen Sie diesen Third" /fastdetect   option being the option that works.

**sudo fdisk -l** output:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x004a004a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       16603   133355565    f  W95 Ext'd (LBA)
/dev/sda2   *       16604       38914   179200000    7  HPFS/NTFS
/dev/sda5   *           2       10199    81915403+   7  HPFS/NTFS
/dev/sda6           10200       10442     1951866   82  Linux swap / Solaris
/dev/sda7           10443       16603    49488201   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e4a2a94

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321   42  SFS
```Ubuntu boots fine. 

So, basicly: when I start my PC, GRUB shows up, I chose Ubuntu, and everything goes normal. But if I wanna go into Windows XP, I need to put a CD. With that CD, Windows works fine.
What I want: to be able to boot Windows from GRUB normally. I mean, when I start my PC and grub shows up, that when I chose "Windows", Windows boots fine, instead of getting Error 12.

Any help? I really don't know what else to do, tried lots of things. =/

Oh, in case it matters, I'm using Ubuntu 9.04. Downloaded and installed it about one month ago.

I think my partition setup is:
1st: a partition with no system files, that I use for music and videos
2nd: a partition subdivided in logic partitions:
2nd-1st: Windows XP
2nd-2nd: Ubuntu Swap
2nd-3rd: Ubuntu

---

### Post by TheStroj on 2009-10-10
When did the problem start? When you installed Ubuntu? Or later when it was already installed?

---

### Post by oldfred on 2009-10-10
You have two windows partitions marked as bootable. One is inside the extended partition. Normally you cannot boot a windows partition that is in an extended partition. The exception I just saw yesterday was someone with three windows partitions, only one was primary. But becasue the extended were Vista & 7 the boot occured on the XP primary and from that boot they could choose the Vista or & in the extended. Their was no way to directly boot Vista or 7.

The only windows stanza that should work is:

title Microsoft Windows XP Professional on sda2
rootnoverify (hd0,1)
savedefault
chainloader +1

---

### Post by louieb on 2009-10-10
This is odd I've never see two partitions have there boot flag turned on at the same time - there should be only one.
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       16603   133355565    f  W95 Ext'd (LBA)
[COLOR=Red]/dev/sda2   *  [/COLOR]     16604       38914   179200000    7  HPFS/NTFS
[COLOR=Red]/dev/sda5   * [/COLOR]          2       10199    81915403+   7  HPFS/NTFS
/dev/sda6           10200       10442     1951866   82  Linux swap / Solaris
/dev/sda7           10443       16603    49488201   83  Linux
```> With multi(0)disk(0)rdisk(0)partition(2)\Windows="3RD TRY THIS wahlen Sie diesen Third" /fastdetect option being the option that works.That tells me that windows is on /dev/sda2 or (hd0,1) in GRUB speech.

> The files in that CD are:
boot.ini WINNT.ini WINXP.ini BOOTCAT.bin BOOTIMG.bin ntdetect.com ntldrThose are windows boot files some I recognize as belonging to XP. 

It is possible to to have a windows install without any boot files in it. That mean GRUB can't boot it. - Did you at one time have two windows installs on the hard drive?

Not a windows boot expert but you need to check your windows install to see if the boot files are there at least boot.ini , ntdetect.com and ntldr.

lol - I'm a windbag - and late - just said the same thing as **oldfred**.

---

### Post by lainmaster on 2009-10-10
The files I have in the CD, I also have in D:\ (where Windows is).

The problem started when I installed Ubuntu.

It might be worse than that, this is what I actually did:

Installed XP (created 3 partitions, 1 for XP, one for just files, 1 for another OS I would later install)
Installed 7
Deleted 7's partition
Created 1 partition for Ubuntu where 7 was. 
Ubuntu told me it needed another partition too, for swap.
Deleted the partition I had just created.
Created 2 partitions where 7 was, one for swap and one for Ubuntu.
Installed Ubuntu.
Used XP's recovery console and ran FIXMBR and FIXBOOT.
Now I had neither GRUB nor XP's boot screen, so I used update-grub. Installed it both to the MBR and Ubuntu's partition, just in case. That got GRUB working again just fine.
And this is where I am now. 

Back when I had XP and 7, I would get 7's boot screen, which would allow me to boot into 7 or XP. That worked fine. 
Since I installed Ubuntu, I was never able to boot into XP without using the CD with the ntldr.

> **oldfred said:**
> The only windows stanza that should work is:

title Microsoft Windows XP Professional on sda2
rootnoverify (hd0,1)
savedefault
chainloader +1

That ones gives me "NTLDR is missing", I think. I'll check now.
EDIT: Yup, I get "Starting up.../NTLDR is missing/press Ctrl+Alt+Del to restart". I guess hd0,1 is the right partition...

EDIT2: GParted screenshot.

[[IMG]http://img3.imageshack.us/img3/2663/screenshotml.png[/IMG]]("http://img3.imageshack.us/i/screenshotml.png/")
In the image, there's only one partition with the boot flag, but that's because I just changed it. When I first opened GParted just now, both Windows XP (sda5) and Files2 (sda2) had the boot flag. By the way, I just now changed the boot flags again. Now, only Windows XP has the boot flag. (Did this AFTER taking the screenshoot).

EDIT3: after setting the boot flag only in Windows XP partition, nothing changed.

---

### Post by lainmaster on 2009-10-11
bump >_>

---

### Post by oldfred on 2009-10-11
Well louieb is the one that lead me to this site that explains your problem.

[http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products](http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products)
louieb's suggestion:
Just a note about dual booting 2 MS products. When you install the 2nd one - the installer will put its boot loader in the partition with the boot flag on (usually the partition holding the 1st MS product). And the 2nd product can only be booted thru the boot loader in the 1st product.

[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

So when you installed Win7, it but the win7 bootloader into the win XP boot. You have to reinstall ntldl for winXP. See the multiboot site for more explanation.

---

### Post by lainmaster on 2009-10-11
I used PowerQuest's Partition Table Editor to manually set the number of Hidden Sectors for Windows XP, and it now boots fine. It was 63, I put it to 63 + the "Sectors Before" for the previous partitions.
But I also seem to have touched something else and now I can't see a partition I used for movies and anime series ¬¬ 
Now, I'm trying to get that partition back. It shows as "Local Disk" in My PC in Windows >_>

---

