---
title: "Grub 2 - rearranging &amp; removing double entries..."
date: 2009-10-31
forum: General Help
---

### Post by chris59 on 2009-10-31
Hi,

I've read several topics which describe how to adjust Grub2 to our needs. I managed to remove the 'recovery', memtest and kernel version entries. Some background image added, colours, etc. But I can't fix two things, which are...

Firstly... How items in Grub2 can be reordered? I would like to move for example Windows 7 entry 'one level up'. How can it be done? In which file should i look up since menu.lst is not present... From what I have read, there is somthing about creating a file which would 'skip' default OS ordering, I don't know...

The second problem is connected with removing a 'bad' entry. I have Windows 7 installed on one partition, Ubuntu on another. The problem is that osprober finds two Windows 7 entries: one located on sda1 (which is a recovery partition) and sda2, on which Windows 7 is installed. What is more, Windows starts only when I launch the entry 'fixed' to sda1 rather than sda2 (launching this entry results with no action), what is weird for me, but ok... I don't care about it. 

fdisk -l

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530        9572    64598058    7  HPFS/NTFS
/dev/sda3            9573       38913   235681582+   5  Extended
/dev/sda5            9573       18058    68163763+   7  HPFS/NTFS
/dev/sda6           18059       37650   157372708+   7  HPFS/NTFS
/dev/sda7           37651       38779     9068661   83  Linux
/dev/sda8           38780       38913     1076323+  82  Linux swap / Solaris

```I've read for example this topic: [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602) , which was quite helpful, but I do not know how to fix these obstacles mentioned above.
Thanks for any help.

Chris

---

### Post by hellmet on 2009-11-25
Solved it? I am not a very big fan of the new Grub. I happen to have two Suse entries - one that is bogus. And I cannot seem to rename the entries, neither can I move them up/down. Pretty frustrating.

---

