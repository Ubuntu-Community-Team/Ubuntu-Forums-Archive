---
title: "Data Recovery &gt; Super-Block Error"
date: 2006-04-29
forum: General Help
---

### Post by marcog on 2006-04-29
This is a follow-on on my problem in [this thread]("http://ubuntuforums.org/showthread.php?t=167789").

As you will see in the thread above I had a disaster with Partition Magic crashing while in the process of moving my Ubuntu partition (ext3). My Windows and Gentoo partitions were not damaged and I can now boot into either.

I am now in the process of attempting to recover the data on my Ubuntu partition. I have spent a full day now trying to sort this out without getting very far. I have tried using fsck, parted, debugfs and some others. Parted picks up my Ubuntu partition, but cannot determine the fs - it identifies it as the size it was before running Partition Magic.

They all give a super-block error stating that the "magic number" is invalid. I have tried using the back-up super-block locations, but none of them work.

Any ideas that you think I should try? Most of the tools available seem to be aimed towards recovery from accidental deletion. I have yet to find one that can solve the kind of problem I am having.

---

### Post by ajgreeny on 2006-04-29
Have you tried looking at your ubuntu partition using explore2fs in Windows.  It may or may not work with a partition that could be messed up, but must be worth a try just in case.  It is a small free download under a gpl license and you can get it at:-
[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)
I use it when I'm in Windows (not often these days), but it can be useful to export files from linux partitions into windows if needed.  Let me know if it works or not.

---

### Post by marcog on 2006-04-29
No, it doesn't work. It only identifies my Gentoo partition and not my Ubuntu partition which is the broken one.

Here is the debug output:

```
Explore2fs version 1.07
Written by John Newbigin
If you experience problems using this program, please set the
debug level to high, restart the program, cause the problem and
then e-mail the debug log and a description of the problem to
John Newbigin jn@it.swin.edu.au
Windows NT 5.1 build number 2600
EXT2 Found. magic = 0xEF53
UID = 21606DF9A35C4C36AF523088E353B893
EXT2 Found. magic = 0xEF53
UID = 21606DF9A35C4C36AF523088E353B893
Looking for Linux Partitions
Using NT_Scan (NT Native IO)
Magic = |ÿ
Magic = ndle::up
\Device\Harddisk0\Partition3
EXT2 Found. magic = 0xEF53
UID = 21606DF9A35C4C36AF523088E353B893
Magic = 
No LVM2 detected
Found 1 ext2/ext3 partitions
```

---

### Post by marcog on 2006-04-30
Any other suggestions? Please.....

---

### Post by marcog on 2006-04-30
An update:

I'm currently running [Data Recovery Wizard Professional]("http://www.easeus.com/download.htm"). It's picking up a whole bunch of files in raw recovery mode, but it's going to take a long time - 24+ hours. And I'm only trying the demo version. Full version costs $100!

Any free alternatives that will recover my files a little quicker?

---

