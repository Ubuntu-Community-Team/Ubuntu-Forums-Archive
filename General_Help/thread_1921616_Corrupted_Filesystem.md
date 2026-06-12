---
title: "Corrupted Filesystem"
date: 2012-02-07
forum: General Help
---

### Post by liptak15 on 2012-02-07
Hey guys, I have a major issue with my Kubuntu (or laptop?). System checks my HDDs after a few boots and almost always finds that the filesystem is corrupted and I have to run fsck manually. So I run fsck /dev/sda2 and there are bunch of errors I have to fix. After reboot the system starts well, but sometimes (once a week or two) some problem starts to occur, e.g. sound isn't working, plasma or kdeinit starts to crash etc...

I have to reinstall the whole system almost weekly :(. My laptop is Lenovo G550 64bit and Kubntu version 11.04.

Thanks for your time!

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda2
fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
/dev/sda2 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Error reading block 524508 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 2097211 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Pass 2: Checking directory structure
Entry 'Qt.so' in /usr/lib/pymodules/python2.7/PyQt4 (133747) has deleted/unused inode 133825.  Clear<y>? yes

Entry 'QtAssistant.so' in /usr/lib/pymodules/python2.7/PyQt4 (133747) has deleted/unused inode 133826.  Clear<y>? yes

Entry 'QtCore.so' in /usr/lib/pymodules/python2.7/PyQt4 (133747) has deleted/unused inode 133827.  Clear<y>? yes

Entry 'QtDeclarative.so' in /usr/lib/pymodules/python2.7/PyQt4 (133747) has deleted/unused inode 133828.  Clear<y>? yes

Entry 'QtDesigner.so' in /usr/lib/pymodules/python2.7/PyQt4 (133747) has deleted/unused inode 133829.  Clear<y>? yes

Entry 'QtGui.so' in /usr/lib/pymodules/python2.7/PyQt4 (133747) has deleted/unused inode 133830.  Clear<y>? yes

Entry 'QtHelp.so' in /usr/lib/pymodules/python2.7/PyQt4 (133747) has deleted/unused inode 133831.  Clear<y>? yes

Entry 'QtNetwork.so' in /usr/lib/pymodules/python2.7/PyQt4 (133747) has deleted/unused inode 133832.  Clear<y>? yes

Entry 'QtScript.so' in /usr/lib/pymodules/python2.7/PyQt4 (133747) has deleted/unused inode 133833.  Clear<y>? yes

Entry 'QtScriptTools.so' in /usr/lib/pymodules/python2.7/PyQt4 (133747) has deleted/unused inode 133834.  Clear<y>? yes

Entry 'QtSvg.so' in /usr/lib/pymodules/python2.7/PyQt4 (133747) has deleted/unused inode 133835.  Clear<y>? yes

Entry 'QtTest.so' in /usr/lib/pymodules/python2.7/PyQt4 (133747) has deleted/unused inode 133836.  Clear<y>? yes

Entry 'QtWebKit.so' in /usr/lib/pymodules/python2.7/PyQt4 (133747) has deleted/unused inode 133837.  Clear<y>? yes

Entry 'QtXml.so' in /usr/lib/pymodules/python2.7/PyQt4 (133747) has deleted/unused inode 133838.  Clear<y>? yes

Entry 'QtXmlPatterns.so' in /usr/lib/pymodules/python2.7/PyQt4 (133747) has deleted/unused inode 133839.  Clear<y>? yes

Entry '__init__.py' in /usr/lib/pymodules/python2.7/PyQt4 (133747) has deleted/unused inode 133840.  Clear<y>? yes



Entry 'events' in /etc/acpi (523366) has deleted/unused inode 523697.  Clear<y>? yes

Entry 'asus-brn-down.sh' in /etc/acpi (523366) has deleted/unused inode 523698.  Clear<y>? yes

Entry 'asus-brn-up.sh' in /etc/acpi (523366) has deleted/unused inode 523699.  Clear<y>? yes

Entry 'asus-touchpad.sh' in /etc/acpi (523366) has deleted/unused inode 523700.  Clear<y>? yes

Entry 'asus-wireless.sh' in /etc/acpi (523366) has deleted/unused inode 523701.  Clear<y>? yes

Entry 'batterybtn.sh' in /etc/acpi (523366) has deleted/unused inode 523702.  Clear<y>? yes

Entry 'ejectbtn.sh' in /etc/acpi (523366) has deleted/unused inode 523703.  Clear<y>? yes

Entry 'hibernate.sh' in /etc/acpi (523366) has deleted/unused inode 523704.  Clear<y>? yes

Entry 'ibm-wireless.sh' in /etc/acpi (523366) has deleted/unused inode 523705.  Clear<y>? yes

Entry 'lid.sh' in /etc/acpi (523366) has deleted/unused inode 523706.  Clear<y>? yes

Entry 'lockbtn.sh' in /etc/acpi (523366) has deleted/unused inode 523707.  Clear<y>? yes

Entry 'mailbtn.sh' in /etc/acpi (523366) has deleted/unused inode 523708.  Clear<y>? yes

Entry 'mediabtn.sh' in /etc/acpi (523366) has deleted/unused inode 523709.  Clear<y>? yes

Entry 'nextbtn.sh' in /etc/acpi (523366) has deleted/unused inode 523710.  Clear<y>? yes

Entry 'playbtn.sh' in /etc/acpi (523366) has deleted/unused inode 523711.  Clear<y>? yes

Entry 'power.sh' in /etc/acpi (523366) has deleted/unused inode 523712.  Clear<y>? yes



Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Inode 523366 ref count is 3, should be 2.  Fix<y>? yes

Unattached inode 523725
Connect to /lost+found<y>? yes

Inode 523725 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523726
Connect to /lost+found<y>? yes

Inode 523726 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523727
Connect to /lost+found<y>? yes

Inode 523727 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523728
Connect to /lost+found<y>? yes

Inode 523728 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523729
Connect to /lost+found<y>? yes

Inode 523729 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523730
Connect to /lost+found<y>? yes

Inode 523730 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523731
Connect to /lost+found<y>? yes

Inode 523731 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523732
Connect to /lost+found<y>? yes

Inode 523732 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523733
Connect to /lost+found<y>? yes

Inode 523733 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523734
Connect to /lost+found<y>? yes

Inode 523734 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523735
Connect to /lost+found<y>? yes

Inode 523735 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523736
Connect to /lost+found<y>? yes

Inode 523736 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523737
Connect to /lost+found<y>? yes

Inode 523737 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523738
Connect to /lost+found<y>? yes

Inode 523738 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523739
Connect to /lost+found<y>? yes

Inode 523739 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523740
Connect to /lost+found<y>? yes

Inode 523740 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523741
Connect to /lost+found<y>? yes

Inode 523741 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523742
Connect to /lost+found<y>? yes

Inode 523742 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523743
Connect to /lost+found<y>? yes

Inode 523743 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523744
Connect to /lost+found<y>? yes

Inode 523744 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523745
Connect to /lost+found<y>? yes

Inode 523745 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523746
Connect to /lost+found<y>? yes

Inode 523746 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523747
Connect to /lost+found<y>? yes

Inode 523747 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523748
Connect to /lost+found<y>? yes

Inode 523748 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523749
Connect to /lost+found<y>? yes

Inode 523749 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523750
Connect to /lost+found<y>? yes

Inode 523750 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523751
Connect to /lost+found<y>? yes

Inode 523751 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523752
Connect to /lost+found<y>? yes

Inode 523752 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523753
Connect to /lost+found<y>? yes

Inode 523753 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523754
Connect to /lost+found<y>? yes

Inode 523754 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523755
Connect to /lost+found<y>? yes

Inode 523755 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 523756
Connect to /lost+found<y>? yes

Inode 523756 ref count is 2, should be 1.  Fix<y>? yes

Pass 5: Checking group summary information
Block bitmap differences:  -2105506
 -(2130184--2130198)
Fix<y>? yes

Free blocks count wrong for group #64 (21704, counted=21705).
Fix<y>? yes

Free blocks count wrong for group #65 (7352, counted=7367).
Fix<y>? yes

Free blocks count wrong (2660363, counted=2660379).
Fix<y>? yes

Inode bitmap differences:  -(133825--133840) -(523697--523712)
Fix<y>? yes

Free inodes count wrong for group #16 (75, counted=91).
Fix<y>? yes

Free inodes count wrong for group #64 (47, counted=63).
Fix<y>? yes

Directories count wrong for group #64 (1082, counted=1081).
Fix<y>? yes

Free inodes count wrong (787953, counted=787985).
Fix<y>? yes


/dev/sda2: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda2: 127727/915712 files (0.2% non-contiguous), 1001445/3661824 blocks
ubuntu@ubuntu:~$ 
```

---

### Post by AlanQ on 2012-02-07
Have you tried running e2fsck with the badblocks option?
(see 'man e2fsck').

---

### Post by liptak15 on 2012-02-08
No, I haven't tried it until now. Here's the output. Does is mean that my HW is ok?


```
ubuntu@ubuntu:~$ sudo fsck /dev/sda2 -c
fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
Checking for bad blocks (read-only test): done                                
/dev/sda2: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes

Running additional passes to resolve blocks claimed by more than one inode...
Pass 1B: Rescanning for multiply-claimed blocks
Multiply-claimed block(s) in inode 397857: 1652504
Multiply-claimed block(s) in inode 413286: 159744 159779
Multiply-claimed block(s) in inode 414374: 1652510
Pass 1C: Scanning directories for inodes with multiply-claimed blocks
Pass 1D: Reconciling multiply-claimed blocks
(There are 3 inodes containing multiply-claimed blocks.)

File /var/tmp/kdecache-ondrej/http/a97c1a4accebd162db0c702361decaa70c35c1cf (inode #397857, mod time Sat Feb  4 17:40:17 2012) 
  has 1 multiply-claimed block(s), shared with 1 file(s):
        <The bad blocks inode> (inode #1, mod time Wed Feb  8 09:34:51 2012)
Clone multiply-claimed blocks<y>? yes

File /var/tmp/kdecache-ondrej/icon-cache.kcache (inode #413286, mod time Wed Feb  8 09:29:46 2012) 
  has 2 multiply-claimed block(s), shared with 1 file(s):
        <The bad blocks inode> (inode #1, mod time Wed Feb  8 09:34:51 2012)
Clone multiply-claimed blocks<y>? yes

Error reading block 159779 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes

Force rewrite<y>? yes

File /var/tmp/kdecache-ondrej/http/51e91b741ec363190c2425d7f9fbb29782b3a177 (inode #414374, mod time Thu Jan 19 08:25:31 2012) 
  has 1 multiply-claimed block(s), shared with 1 file(s):
        <The bad blocks inode> (inode #1, mod time Wed Feb  8 09:34:51 2012)
Clone multiply-claimed blocks<y>? yes

Error reading block 1652510 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes

Force rewrite<y>? yes

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong for group #0 (23178, counted=23174).
Fix<y>? yes

Free blocks count wrong for group #4 (14931, counted=14933).
Fix<y>? yes

Free blocks count wrong for group #50 (6994, counted=6996).
Fix<y>? yes


/dev/sda2: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda2: 130234/915712 files (0.2% non-contiguous), 1080440/3661824 blocks
ubuntu@ubuntu:~$ 
```

---

### Post by Herman on 2012-02-08
A new hard disk would probably fix it.

If you have enough money, just go and buy one, but if you're short of cash it might be worth the time to test it first and see if you can confirm it's really worn out or damaged.

Disk Utility in Ubuntu gives us a nice way to check, it's not accurate for all brands of HDD though, notably Seagate drives. Those can give a misleading report.

The badblocks command is a more reliable test to find out if your hard disk is about to fail,
```
sudo badblocks /dev/sda1
```Feel free to replace the 1 at the end of /dev/sda1 with any partition number you want.
The badblocks command can check the entire disk if you just tell it /dev/sda, or /dev/sdb etc, but it takes a long time so one partition at a time is usually enough.
If it doesn't produce any output your hard disk is okay, but if it reports a lot of bad sectors then you can be sure you need to go buy a new hard disk.

---

### Post by liptak15 on 2012-02-08
Thanks for your reply. It's a laptop - Lenovo G550 - and still in warranty. The badblocks command didnt't produce any output (thank God).So I assume, my HDD is ok. 
It started to occur after I formated the whole HDD and installed WinXP and Kubuntu.:-k

---

### Post by Herman on 2012-02-08
Okay it fooled me then, the rest of your story sure does make it sound like a faulty hard disk drive would be the most likely cause of your problems. I wouldn't rule out that possibility just yet, even if the machine is new. If it's still under warranty you have all the more reason to want to be fairly certain your hard drive is okay before the warranty runs out. 

The following command can find out the name of the hard drive vendor and other details about the drive (without having to unscrew any hatches from the bottom of the laptop),
```
sudo lshw -C disk
```Most hard disk drive manufacturers have their own diagnostic software available from their websites for free.

---

### Post by Herman on 2012-02-08
> It started to occur after I formated the whole HDD and installed WinXP and Kubuntu.:-kA normal hard disk drive should be able to easily handle having operating systems installed and re-installed hundreds of times. I know that for sure because I have old computers here that still have the original hard drives in them. I have a website about how to install Ubuntu and I have to install and re-install Ubuntu a good number of times to make sure I know what I'm talking about when I want to update my website. (I've been a little short on time for that lately but I'll get back to it sometime soon, for 12.04 I hope. :)

---

