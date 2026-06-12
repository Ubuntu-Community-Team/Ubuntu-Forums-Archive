---
title: "How did my i-nodes get so messed up?"
date: 2009-12-24
forum: General Help
---

### Post by rpaskudniak on 2009-12-24
Greetings.

Twice this week I have had to run fsck on my /home file system because of a complaint while booting and mounting it.  The first time, I needed to delete my .gconfd directory so that a new one would be created, followed by manually recreating my gnome environment. (Solution posted in another thread, not started by me.)

The second time, last night, I decided to boot up in recovery mode and preserved the fsck output by using the "script" command.  I am including it with this post.  The big question to me is: How did my i-nodes get so messed up?  How did the reference counts and free block counts go bad?  How did some files get turned into the symbolic links and how did they suddenly develop the wrong file type?

This could be related to a crash but still makes no sense.

Clues?

In any case, FWIW, here is the output of fsck.  BTW, I saved it using:
# script fsck.out
Then, after fsck is done, remembering to ctrl-D.

```
[SIZE="1"]Script started on Thu Dec 24 07:54:20 2009
root@chief:/usr/data# fsck
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda3 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda4 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Entry 'Error for FireFox-1.png' in /jake/Desktop (2367499) has an incorrect filetype (was 1, should be 2).
Fix<y>? yes

Entry 'Error for FireFox-1.png' in /jake/Desktop (2367499) is a link to directory /jake/.mozilla/firefox/q43bcuii.default/extensions/SQLiteManager@mrinalkant.blogspot.com/chrome/skin (2368840).
Clear<y>? yes

Entry '90fd2382a037e43b6aeeaa77c72cdea5.png' in /jake/.thumbnails/fail/gnome-thumbnail-factory (2367651) has deleted/unused inode 2368838.  Clear<y>? yes

Entry '.viminfo-save' in /jake (2367489) has an incorrect filetype (was 1, should be 2).
Fix<y>? yes

Entry '.viminfo-save' in /jake (2367489) is a link to directory /jake/.gconf (2367779).
Clear<y>? yes

Entry 'ksnapshotrc' in /jake/.kde/share/config (2392067) has deleted/unused inode 2393153.  Clear<y>? yes

Entry 'kwin_10c9686965000125838020500000168770000_1261527567_293457' in /jake/.kde/share/config/session (2465989) has an incorrect filetype (was 1, should be 2).
Fix<y>? yes

Entry 'kwin_10c9686965000125838020500000168770000_1261527567_293457' in /jake/.kde/share/config/session (2465989) is a link to directory /jake/.gconfd (2466549).
Clear<y>? yes

Entry 'system' in /jake/.cache/checkbox (2474501) has an incorrect filetype (was 1, should be 7).
Fix<y>? yes

Entry 'submission' in /jake/.cache/checkbox (2474501) has an incorrect filetype (was 1, should be 2).
Fix<y>? yes

Entry 'submission' in /jake/.cache/checkbox (2474501) is a link to directory /jake/.wine/drive_c/windows/system32/spool/drivers/w32x86/3 (2474552).
Clear<y>? yes

Entry 'subunit.log' in /jake/.cache/checkbox (2474501) has an incorrect filetype (was 1, should be 2).
Fix<y>? yes

Entry 'subunit.log' in /jake/.cache/checkbox (2474501) is a link to directory /jake/.wine/drive_c/windows/system32/spool/drivers/win40 (2475062).
Clear<y>? yes

Entry 'checkbox.xsl' in /jake/.cache/checkbox (2474501) has an incorrect filetype (was 1, should be 2).
Fix<y>? yes

Entry 'checkbox.xsl' in /jake/.cache/checkbox (2474501) is a link to directory /jake/.wine/drive_c/windows/system32/spool/drivers/win40/0 (2475063).
Clear<y>? yes

Entry 'plugins.bpickle' in /jake/.cache/checkbox (2474501) has an incorrect filetype (was 1, should be 2).
Fix<y>? yes

Entry 'plugins.bpickle' in /jake/.cache/checkbox (2474501) is a link to directory /jake/.wine/drive_c/windows/profiles/jake/Application Data/Black Sea Studios/Knights Of Honor Demo (2475065).
Clear<y>? yes

Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Inode 2367718 ref count is 1, should be 2.  Fix<y>? yes

Unattached inode 2368783
Connect to /lost+found<y>? yes
Inode 2368783 ref count is 2, should be 1.  Fix<y>? yes

Inode 2368809 ref count is 1, should be 2.  Fix<y>? yes

Inode 2368845 ref count is 1, should be 2.  Fix<y>? yes

Inode 2466547 ref count is 1, should be 2.  Fix<y>? yes

Inode 2474518 ref count is 1, should be 2.  Fix<y>? yes

Inode 2475064 ref count is 1, should be 2.  Fix<y>? yes

Pass 5: Checking group summary information
Block bitmap differences:  +9470540 -(9474190--9474191) +(9476185--9476186) -(9480915--9480917) -9480919 +9480948 -9480949 -9482544 -(9484431--9484443) -(9484449--9484535) -(9484538--9484650) -(9484992--948
5143) -(9485260--9485292) -(9488437--9488439) -(9492598--9492605) -(9492614--9492627) -9589028 -9589186 -9667074 -9699842 -9699845 -9771031 -(9771034--9771035) -9771037 +9771040 +(9771046--9771047) -9773718
 -(9773720--9773721) -9867361 +(9922576--9922588)
Fix<y>? yes

Free blocks count wrong for group #289 (23961, counted=24388).
Fix<y>? yes

Free blocks count wrong for group #290 (9912, counted=6337).
Fix<y>? yes

Free blocks count wrong for group #292 (40, counted=42).
Fix<y>? yes

Free blocks count wrong for group #295 (2, counted=3).
Fix<y>? yes

Free blocks count wrong for group #296 (3, counted=4).
Fix<y>? yes

Free blocks count wrong for group #298 (11278, counted=10042).
Fix<y>? yes

Free blocks count wrong for group #301 (23540, counted=23541).
Fix<y>? yes

Free blocks count wrong for group #302 (25214, counted=25201).
Fix<y>? yes

Free blocks count wrong for group #375 (32256, counted=32253).
Fix<y>? yes

Free blocks count wrong (16397566, counted=16393171).
Fix<y>? yes

Inode bitmap differences:  -2368828 -2393153 -2466548
Fix<y>? yes

Free inodes count wrong for group #289 (6683, counted=6684).
Fix<y>? yes

Free inodes count wrong for group #292 (7089, counted=7091).
Fix<y>? yes

Free inodes count wrong for group #301 (7215, counted=7216).
Fix<y>? yes

Free inodes count wrong for group #375 (8194, counted=8191).
Fix<y>? yes

Free inodes count wrong (4376044, counted=4376045).
Fix<y>? yes


/dev/sda4: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda4: 6675/4382720 files (4.3% non-contiguous), 1109646/17502817 blocks

root@chief:/usr/data# exit

Script done on Thu Dec 24 08:01:16 2009
[/SIZE]
```

---

### Post by cariboo on 2009-12-24
It may be that your hard drive is failing. I would suggest you go to the hard drive's manufacturers web site and download the diagnostic tool and run it on the hard drive.

---

