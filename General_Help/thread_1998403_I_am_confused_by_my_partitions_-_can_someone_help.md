---
title: "I am confused by my partitions - can someone help?"
date: 2012-06-06
forum: General Help
---

### Post by Skara Brae on 2012-06-06
Hello to everyone,

I am aware that this must sound very much like something a n00b would ask (especially if it is asked by someone who has been using Ubuntu since Gutsy Gibbon :p), but I need some help.

I am running Ubuntu 10.04, Xubuntu 10.04 and XP Home in "triple boot" on a single 500 GB HD, and I am confused by the partitions on the HD.

**fdisk -l** shows this:

sda1 - the XP partition (NTFS)
sda2 - "Linux"
sda3 - "Linux"
sda4 - an extended partition
sda5 - "Linux"
sda6 - the swap partition (Linux swap/Solaris)
sdb1 - a second, 80 GB HD used for backup.

**sda1**, **sda4** and **sda6** are clear to me, as is **sdb1**.

**sda2** is Ubuntu - or so I think. I am pretty sure it is Ubuntu (but not 100%). Back in 2007, I installed Ubuntu (Gutsy Gibbon) first, so **sda2** is Ubuntu, I assume (but since assumption is the mother of all FU's . . . )

What exactly is **sda3**? Is it a separate partition for /home in Ubuntu? I don't remember having put /home on its own partition, back in 2007 with "Gutsy".
- How can I find out if sda3 is indeed /home?

**sda5** is Xubuntu 10.04 - or so I think. I am pretty sure it is Xubuntu. But I am not 100% sure, and assumptions are the mother of etc, etc. . .

Nautilus/Ubuntu shows the "WINDOWS" partition; a "105 GB Filesystem"; a "80 GB Filesystem", and the second 80 GB harddrive.
Four names, but five "sda" names?
**sda2** - 105 GB/Ubuntu?
**sda4** - 80 GB/Xubuntu(sda5) & swap(sda6)?
**sda3** - ? (/home?)

And as if it is not confusing enough, Xubuntu sees **sda2** as a root partition (**"/"**) and **sda5** as **/home** (sda5 is /home? What /home? I was assuming that sda3 is a /home partition (of Ubuntu)...)
- Or is sda2-in-Xubuntu sda5-in-Ubuntu, and is sda5-in-Xubuntu sda3-in-Ubuntu (Ubuntu /home)?

So, I am kind of (very) confused by the partition table. How do I find out for sure that (in Ubuntu) **sda2** is Ubuntu and that **sda5** is Xubuntu? And that sda3 is /home in Ubuntu? *lol* See what I mean?

I am confused. Can someone help me shed some light?

---

### Post by drs305 on 2012-06-06
An easy way to determine part of what you want is just to mount the partition and take a look. If you can boot into one of your Linux OS's just run the commands from a terminal, otherwise boot a LiveCD or rescue CD of some time and open a terminal.
```

sudo mkdir /mnt/test
sudo mount /dev/sda2 /mnt/test
sudo cat /mnt/test/etc/fstab
```
The last command will show you what that OS mounts. If you see a separate listing for /home, check if it's sda3. 

If there is no separate home listing, unmount /dev/sda2 and try sda3.
```
sudo umount /dev/sda2
sudo mount /dev/sda3 /mnt/test
```
If you mount sda3, the contents of /mnt/test/ should show a recognizable username as one of the /mnt/test folders.

If you inspect sda5, check /mnt/test/etc/lsb_release. I can't remember if it will list the OS as Xubuntu or not (I'm thinking not), but you can check.

---

### Post by Skara Brae on 2012-06-06
drs305,

It took me a while. This is quite "under the hood" for me, meaning, I am not sure what this tells (me). I'm now really using my brain (what a difference with "that other OS" :P)

Ok, so with **sda2**, I get this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type>  <options>   <dump>  <pass>
proc            /proc         proc    defaults    0       0
# /dev/sda2
UUID=acdc1930-3c59-4ea0-ae32-30e0b1ee7d9d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1c5d4961-ff0e-4198-ab43-6747c4a7710f /home           ext3    relatime        0       2
# /dev/sda6
UUID=e1601bdc-ca41-4ff3-b069-4ef073671a24 none            swap    sw              0       0
```

(It looks abit messy this way)

I left out the floppy drive and my DVD-rom and DVD-rewriter (scd0, scd1 and fd0: those are obvious to me).

With **sda3**, I get:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=154f05eb-10c2-4a3a-ab1f-912640a42081 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 installation
UUID=e1601bdc-ca41-4ff3-b069-4ef073671a24 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#daar stond "noauto" tussen, zoals hieronder
#"noauto" er terug in gezet (zoals op ubuntuforums.org vermeld).
/dev/sdd        /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0
```

(Uhm, ok, ignore the lines in that "foreign" language: those are comments I added in my native language Dutch. I remember doing that, but not why (nevermind that).
Why don't I see any scd0/DVD-rewriter and scd1/DVD-rom in there?
What is /dev/sdd?)

**sda6** is swap. swap for both Ubuntu and Xubuntu? Ah yes, I remember having read that different installs can use one swap partition.

-oo-

To conclude, and do correct me if I am wrong:
- Ubuntu has no separate /home. Ubuntu is **sda2**.
- Xubuntu is **sda3**.
- Xubuntu does have a separate /home. It is **sda5**.
- The "80 GB Filesystem" in Nautilus is **/home** of Xubuntu. It is **sda5**.
- The "105 GB Filesystem" in Nautilus is Xubuntu.  The folder /home in there is empty (since /home in Xubuntu is a separate partition.)

On a sidenote: when I mount that "80 GB Filesystem" in Nautilus, then I see the /home from Xubuntu: I recognize my files.
When I mount that "102 GB Filesystem" in Nautilus, then I see Xubuntu (where /home is empty).

I remember that I once had a /home for both Ubuntu and Xubuntu: it gave me difficulties with desktop settings and stuff...

drs305,
I think that you have helped me a **lot**. Without your help, I never would have gotten it. Very much obliged, drs305!

---

### Post by drs305 on 2012-06-06
Your sda2 fstab shows the following:
> # **/dev/sda2**
UUID=acdc1930-3c59-4ea0-ae32-30e0b1ee7d9d **/**               ext3    relatime,errors=remount-ro 0       1
# **/dev/sda5**
UUID=1c5d4961-ff0e-4198-ab43-6747c4a7710f **/home**           ext3    relatime        0       2
# **/dev/sda6**
UUID=e1601bdc-ca41-4ff3-b069-4ef073671a24 none            **swap**

I think you have it sorted out.

First, the disclaimer. The # notes which show the /dev partition do not get updated if the partitions are moved, so they are no *absolutely* assured to be accurate. But normally they are. You can compare the partition and UUIDs to see if they still match by running "sudo blkid".

Now, the above shows an Ubuntu installation on sda2 ( / ) with it's home being on sda5 (/home) and a swap on sda6 (swap).

Your second output shows a complete installation on sda3:
> # / was on **[B]/dev/sda3**[/B] during installation
UUID=154f05eb-10c2-4a3a-ab1f-912640a42081 **/**               ext3    errors=remount-ro 0       1

There is no separate listing for **/**, so we can safely assume that it's "home" is not separate and is on the main partition (sda3).

---

### Post by oldfred on 2012-06-06
I like to run Bootinfo script to document my system. And I like to label partitions so I know what is in each partition when I create or change it.

drs305 has links to BIS Boot info Script and Boot Repair which also can run Boot info script. The report is long, but has lots of details, sometimes takes a while to know what is where.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

You can add labels with gparted or Disk Utility. Of course I have a few more installs than you, but I have installed to the wrong partition until I learned to label & printout a list of the labels rather than try to remember which is which.

```
fred@fred-Precise:~$ sudo blkid -c /dev/null -o list
[sudo] password for fred: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    WinXP    /mnt/cdrive    04B05B70B05B6768
/dev/sda2  ext3    backup   (not mounted)  13a684e4-2849-4566-9528-21cd07028a9a
/dev/sda4  vfat    SHARE    (not mounted)  46CD-C9B2
/dev/sdb2  ext4             /media/d1350acd-12ce-4004-9039-4ce87d8787b5 d1350acd-12ce-4004-9039-4ce87d8787b5
/dev/sdb3  ext4    KingstonData /media/KingstonData 4215f5b3-ce4c-4ef8-bc1a-0daac816fb75
/dev/sdb4  ntfs             /media/5FE046DD43C03A7C 5FE046DD43C03A7C
/dev/sdc2  ext4    Maverick (not mounted)  0eea4e95-ea0a-4745-80d4-57bf2bbc9d69
/dev/sdc3  swap             (not mounted)  00c4e383-cf30-4b54-9a9f-d46953e3966e
/dev/sdc4  ext4    MavData  (not mounted)  431ba9e5-c72c-41c2-ba82-d8ee052336ff
/dev/sdd1  ext3    grub     (not mounted)  9e16ad9c-c5f8-4b5a-b2b3-20dfc71a422f
/dev/sdd2  ntfs    Shared   /mnt/shared    44332FD360AA9657
/dev/sdd4  ext2    bios_gpt (not mounted)  bbda6045-bb8a-4666-8bd4-04b3945ca581
/dev/sdd5  ext4    Karmic   (not mounted)  117412d5-2dbe-4011-8aec-ae310d1ee6c7
/dev/sdd6  ext3    Data     /mnt/data      a55e6335-616f-4b10-9923-e963559f2b05
/dev/sdd7  ext4    LUCID    (not mounted)  5e25282c-9c54-45df-9e79-514011e98648
/dev/sdd8  ext4    Test     (not mounted)  af29c61a-34e9-48eb-9c94-afcb4bb61582
/dev/sdd9  vfat    OLDG     (not mounted)  F6A6-705D
/dev/sdd10 ext4    newhome  (not mounted)  b8a7e331-a716-4ac1-bf58-6ac515606c6d
/dev/sdd11 swap             <swap>         09367687-86d1-4fd0-9b81-2787d3196159
/dev/sdd12 ext4    Puppy    (not mounted)  07e2a08d-37ca-4cf1-877b-f02b0eabcbca
/dev/sdd13 ext4    natty    (not mounted)  318fd41e-4210-4960-a0d9-ee9b48388d69
/dev/sdd14 ext4    kubuntu  (not mounted)  2b42c9ad-4304-4a8a-8991-08cfe35717ec
/dev/sdd15 swap             <swap>         2c05178d-1e0e-4ae8-80e6-a700dc0d6eb9
/dev/sdd16 ext4    oneiric  (not mounted)  63d146fd-1c63-4b31-95c5-ab52e2892283
/dev/sdd17 ext4    server   (not mounted)  63045773-e42a-46eb-9e96-b93428542527
/dev/sdd18 ext4             (not mounted)  117e0c31-7e16-4e8b-90b7-a3c688a34f26
/dev/sde1  vfat    EFI      (not mounted)  7B30-5ACA
/dev/sde3  ext4    Precise  /              adc013e9-a23d-4a36-849b-3faeac005667
/dev/sde4  ext4    quantal  (not mounted)  3b72e3d4-3d56-469b-ad50-f13ac4f5f0d4



```

---

### Post by Skara Brae on 2012-06-08
> **drs305 said:**
> Now, the above shows an Ubuntu installation on sda2 ( / ) with it's home being on sda5 (/home) and a swap on sda6 (swap).

Your second output shows a complete installation on sda3:

There is no separate listing for **/**, so we can safely assume that it's "home" is not separate and is on the main partition (sda3).
Well, **drs305**, pity that I did not read your message sooner :)

[quote=Skara Brae]To conclude, and do correct me if I am wrong:
- Ubuntu has no separate /home. Ubuntu is sda2.
- _**Xubuntu is sda3.**_
- Xubuntu does have a separate /home. It is sda5.
- The "80 GB Filesystem" in Nautilus is /home of Xubuntu. It is sda5.[/quote]

Murphy's Law has struck. Xubuntu was indeed not **sda3**, but **sda2**. Ubuntu was **sda3**. And Xubuntu's /home on **sda5**.

I wanted to keep Ubuntu and XP and "have fun" and use the Xubuntu partition to try another Linux distro (Fedora 17). Earlier this week, I installed Xubuntu over XP Home on an old P4 machine of mine, so why keep two Xubuntu installs?

So, I installed Fedora on sda3.

Fedora messed up the GRUB loader (I chose not to install GRUB in the Fedora installer--or something like this; can't remember by heart). I got a black screen with:

```
Booting from local disk...

error: file not found.
grub rescue>
```

Yikes.

To keep it short, I followed your (**drs305**) excellent thread about how to fix GRUB (as in *showthread.php?t=1195272*), and after rebooting my PC, I get the list of the Linux/XP installations (with a new, blue, Debian background picture). I picked Ubuntu 10.04, and Xubuntu starts...

**sda3** was indeed not Xubuntu, but Ubuntu.

Yikes, indeed.

I had backed up Xubuntu's /home, since I didn't know/remember that Xubuntu's /home was a separate partition. But I had not backed up my Ubuntu's /home. Can you see it coming? :p Yeah, my Ubuntu's /home is gone... (When did I make the last backup?)

For **once** I didn't back every up, aaargh.

As I said: Murphy's Law.

Damm you, Murphy, I hate you :P

It's okay. There are *lots* of worse things. I'll just start over with Ubuntu (unless someone has a magic wand?).

I haven't tried Fedora 17 yet. It is the GRUB list too. It had better be worth losing Ubuntu's /home.

---

### Post by drs305 on 2012-06-08
Well, perhaps sharing your experiences will prevent another user from repeating your troubles.

Happy Ubuntu-ing.

---

### Post by Skara Brae on 2012-06-08
> **drs305 said:**
> Well, perhaps sharing your experiences will prevent another user from repeating your troubles.
Other n00b'ish users, you mean :) They **must** be certain *which* partition contains *what*. Double-check, and check again. And make backups! :)

-oo-

Ubuntu rocks. It is my experience that it is the finest Linux distro (of the few) that I have experience with, as is Xubuntu.

Fedora 17 won't work; I see a kernel panic during boot (bla bla bla, "VFS: Cannot open root device "sda3" or unknown-block(0,0). Please append a correct "root=" boot option; here are the available partitions: Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block. bla bla bla). Nevermind. I will format Fedora's partition later.

Win XP boots fine (GRUB says it is Vista, as it did long, long ago.)

My last backup from my /home in Ubuntu dates from May 1. I've lost a few files, but nothing dramatic (whew!).

I think we can close up this thread now.

> **drs305 said:**
> Happy Ubuntu-ing.
Thank you, drs305. I am sure that I will :) I really like Ubuntu (and Xubuntu).

---

