---
title: "Possible tough challenge..."
date: 2010-06-12
forum: General Help
---

### Post by BadGene on 2010-06-12
Greetings. I have a dual boot with windows 7 (same disk) and I messed up something big time! Don't ask me how but I found suddenly that System's Preferences and Administration have disappeared... So, has I'm in my first weeks with Linux I don't have much important data in and I decided to re-install. I did that but now I can't access windows 7! The Windows Boot Manager kicks in saying:
 
"Windows failed to start. A recente hardware or software change might be the cause. To fix the problem:
1. Insert windows installation disc and restart your computer.
2. Choose your language settings, and then click "Next"
3. Click "Repair your computer."
 
Status: 0xc000000f
Info: The boot selection failed because a required device is inaccessible."
 
Repairing with Windows disc is useless...
 
I have some important files I would like to backup in windows file system (Documents and in the desktop).
 
Is there any way to repair windows boot manager or at least access, through Ubuntu, the windows Documents and Desktop to backup the files in there to an external disk?

---

### Post by clrg on 2010-06-12
I guess your NTFS partition has been messed up. 

But as every responsible computer user honoring the countless warnings I'm sure you've been given, I'm sure you did a backup before you messed around with the partitioning? :grin:

---

### Post by BadGene on 2010-06-12
I've made a backup more than a month ago... Meanwhie, I've created several important files. I don't believe I touched the windows partition. Just reinstalled Ubuntu. As I did a few times in a few different computers. Never has this happenned.

---

### Post by BadGene on 2010-06-13
So, any suggestion on how to correct this or to access files in windows through linux or something?

---

### Post by spiky001 on 2010-06-13
can you boot in to ubuntu then acsess windows from there? If not use live cd to get files from windows

---

### Post by prodigy_ on 2010-06-13
You can use **chkdsk** command from Windows Recovery Console to check your boot partition for errors.

---

### Post by BadGene on 2010-06-13
@spiky001:
I can explorer a little bit of the partition where Windows is installed but if I go down a few levels all the files are in the form of broken links (My music, my Pictures, My Videos, Cookies, History, Start Menu, etc) and can't go further. Is there other way to access windows apart from exploring the folders and directories?

 Windows Live CD (I presume is the CD from which I installed Windows, right?) tries to repair and it says it can't repair the computer automatically.
_________________________________________________________________________

@prodigy_:
when I enter chkdsk in Windows System Recovery Options' Command Prompt (from the installation disk) it says:

"Windows has checked the file system and found no problems.

   3086 kb total disk space.
        4 kb in 9 indexes.
        0 kb in bad sectors.
   2485 kb in use bt the system.
   2048 kb occupied by the log file.
     597 kb available on disk

    512 bytes in each allocation unit.
   6173 total allocation units on disk.
   1195 allocation units available on disk.
Failed to transfer logged message to the event log with status 50."

Which makes no sense since this is 500GB Hard Drive, 32 GB partition with Ubuntu and the rest with windows 7...
__

---

### Post by spiky001 on 2010-06-13
I presume you want to retrieve the files before trying to fix?
Can you see the files you want can you copy them somewhere safe

---

### Post by BadGene on 2010-06-13
Yes, I would like to retrieve the Documents and Desktop folders. But in Ubuntu the Documents folder only has inside broken link files of My Music, Video and Pictures (all around 100 kb...).  And occurs an error if I try to copy them.

---

### Post by spiky001 on 2010-06-13
have you tried with terminal

---

### Post by BadGene on 2010-06-13
In terminal I have these reply.

"bash: cd: cd: No such file or directory"

Strangely I can go a little more deeper if I explorer the folders with the mouse before I get broken link files.

---

### Post by spiky001 on 2010-06-13
did you mount the windows file system then 
```
cd /media/window partition
```

---

### Post by BadGene on 2010-06-13
Precisely.

---

### Post by prodigy_ on 2010-06-13
Probably you ran chkdsk on a wrong partition. Use ```
diskpart
``` command to enter MS DiskPart interactive mode and then (from **DISKPART>** prompt) ```
list volume
``` command to see which NTFS partitions are available.

---

### Post by spiky001 on 2010-06-13
dont know how your gonna copy files then, apart from whole folders then look in them on ubuntu partition

---

### Post by BadGene on 2010-06-13
> **prodigy_ said:**
> Probably you ran chkdsk on a wrong partition. Use ```
diskpart
``` command to enter MS DiskPart interactive mode and then (from **DISKPART>** prompt) ```
list volume
``` command to see which NTFS partitions are available.



The windows partition was detected and "Status" is "Healthy"...

Any idea on how to proceed?

---

### Post by prodigy_ on 2010-06-13
Try to copy your files (with a data recovery utility) to another drive and then reinstall Windows.

---

### Post by BadGene on 2010-06-13
> **prodigy_ said:**
> Try to copy your files (with a data recovery utility) to another drive and then reinstall Windows.

What utility do you suggest? (from Linux since I can only operate with Ubuntu, now)

---

### Post by spiky001 on 2010-06-13
Have a read through this they are using test disk
[http://ubuntuforums.org/showthread.php?t=387922&highlight=data+recovery](http://ubuntuforums.org/showthread.php?t=387922&highlight=data+recovery)

---

### Post by praveenthivari on 2010-06-13
Did u Use a lve cd and try to access the windows drive

---

### Post by BadGene on 2010-06-13
> **praveenthivari said:**
> Did u Use a lve cd and try to access the windows drive

Windows Live CD? Yes, no practical results.

@Spiky001, Prodigy_:

Thanks for the help. That testdisk discution appears to have a lot of potencial to solve this problem. I'll read it a couple of times and try to make no mistakes. I have other pressing issues to address to now. If you remember other alternatives please post them here. I'll be passing by in the near future.

---

