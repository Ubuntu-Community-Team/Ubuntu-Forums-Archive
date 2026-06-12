---
title: "Windows xp boot disk ruined my hard drive"
date: 2011-07-07
forum: General Help
---

### Post by Mahkoe on 2011-07-07
I used a windows xp boot disk, but I had to do something before all the files were loaded. I come back and says something about setup, so I quit. I am now on an Ubuntu live CD and when I open gparted, it says my whole hard drive is unallocated, and there is a warning saying the disk label is not recognized. I know this might not be the right forum, but I am panicking. Like, hyperventilating panicking. I have not done anything to my hard drive just yet in case that will ruin any chances of recovery.

More details:
Before the hard drive catastrophe, my hard looked a bit like this:
NTFS 14 GB Recovery partition
NTFS 100 MB SYSTEM RESERVED
NTFS 125 GB Windows partition (Windows 7, 64 bit)
Extended partition:
{
Linux-swap 6 GB
Ext2 175 GB Ubuntu partition (10.10, 32 bit)
}
I am on an ubuntu 10.10 (32 bit) live cd. I am using an acer laptop with a Gateway motherboard. My processor is an intel i3, I have 4GB DDR3 RAM, I do have access to booting floppy disks and CDs and flash drives, if that helps. I do not have a windows installation disk, but I do have a recovery disk (Windows7, 64 bit). My hard dricve is supposed to be 320 GB, but after the hard drive catastrophe, (I don't know if it was like this before) it now says it has 300 GB. The boot disk that I used was a windows xp floppy boot disk, no. 1 of 6 from allbootdisks.com.

If you are wondering why I used boot disks, it was because I completely misunderstood what a boot disk was, even with its self-explanatory name. That was ridiculously stupid, and now I am panicking. PLEASE HELP THANK YOU IN ADVANCE

---

### Post by Mahkoe on 2011-07-07
Also, if worst comes to worst, I am prepared to just reinstall ubuntu (windows sucks anyway, although I would like my data). However, I have had this problem on a memory stick where after trying to format it became completely unreadable. Should there be no hope for my data, I would like to know how to format my drive to avoid any Horrible effects. THANKS

Also note that if I need to install a program to fix this, I do have a memory stick I can install ubuntu on. I'll try almost anything.

---

### Post by westie457 on 2011-07-07
> **Mahkoe said:**
> Also, if worst comes to worst, I am prepared to just reinstall ubuntu (windows sucks anyway, although I would like my data). However, I have had this problem on a memory stick where after trying to format it became completely unreadable. Should there be no hope for my data, I would like to know how to format my drive to avoid any Horrible effects. THANKS

Also note that if I need to install a program to fix this, I do have a memory stick I can install ubuntu on. I'll try almost anything.

Hi. Before you kiss good-bye to all your data try something called 'testdisk' available in the repositories. It runs in a terminal. I suggest you run it twice. The first time is only to check what it finds and then if you are happy with it run it again allowing it to fix your hard drive.

If your hard drive is not repairable according to 'testdisk' then run 'photorec' in a terminal as well to recover your data. Save everything to an external drive not the one you have trouble with. 

Here is a link to the testdisk site.[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by Mahkoe on 2011-07-07
Okay, I am officially no longer panicking and am comfortably relaxed, I found a youtube video hidden deep inside a google search explaining how to use testdisk and it is working. Have a nice day

---

### Post by Mahkoe on 2011-07-07
Sorry, I didn<t reload the page and didn\t see your post before I posted, but yeah. thanks.

---

### Post by Mahkoe on 2011-07-07
Thank you to the ubuntu community and the selfless people who on their own time help people who need it.

---

### Post by westie457 on 2011-07-07
> **Mahkoe said:**
> Thank you to the ubuntu community and the selfless people who on their own time help people who need it.

Your welcome. Always remember not to panic. Most situations can be remedied. Sometimes it just takes a while for someone to respond to the first post. Feel free to come back and post with any computer related problems.

---

