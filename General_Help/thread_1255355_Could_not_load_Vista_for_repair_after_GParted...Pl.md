---
title: "Could not load Vista for repair after GParted...Please HELP!"
date: 2009-09-01
forum: General Help
---

### Post by mimitam on 2009-09-01
My Goal:

I have dual boot Vista Home Premium and Ubunto on my laptop working fine until Ubuntu complained that there was no disk space left to do anything. So, I used the GParted Live CD to shrink my C drive which has Vista on it, in order to make room for Ubuntu.

My Problem:

--  I shrunk my C drive using GParted Live CD to shrink it from 133 GB to 96 GB.

--  Then, I used my Vista Boot CD (tested to be good) to try to boot up Vista and expecting an ERROR from Windows, so I could use my Vista Boot CD to repair it.

--  Instead, I was on the "Paragon System Backup 2010" screen already doing a backup (I should mention that my bios - Boot Sequence has only CD boot enabled.) After backup was done, it prompted me to pick an OS to boot. I picked Vista and it prompted me for a .pdf archive file. I don't think I have one.

--  At this point, I exited and rebooted and went back to the same screen where I was stuck.

2 things caught my eyes at boot Setup:

1.   Under "Memory Info", there is a NOTE saying "Due to an amount of memory being assigned for system use, Memory Available is less then Memory Installed. Note that certain operating systems may not be able to use all the available memory. None of these fields are changeable".

2.   Under Boot Sequence, I had only specific my DVD to be the only one in the boot sequence.

Please kindly HELP! I am stuck! I don't want to further mess things up by continuing to try things out. Am I doomed?

Any ideas, suggestions would be greatly appreciated.

Many Thanks....Mimi

---

### Post by bacardiandwatermelon on 2009-09-01
Man that doesnt sound good, I would have used the vista Disk management tool, or something like partition magic 8, I don't think Gparted saves data when you resize a partition. From memory Vista needs SP1 before it will regonise more than 3.3 GB on a 32Bit platform, this maybe related to the memory error you are getting.. Is the Vista dvd booting at all?

---

### Post by mimitam on 2009-09-01
I used the original Vista OS DVD to reboot for repairing Vista. It worked.:)

Thanks.

---

