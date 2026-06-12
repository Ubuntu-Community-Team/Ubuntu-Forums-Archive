---
title: "Properties show me different filesystem Type"
date: 2009-09-23
forum: General Help
---

### Post by molavec on 2009-09-23
Hi people:

I had a problem and when I was trying to resolved I found a situation that confused me at all. 

I have a disk in ext2 filesystem type. I used this one to share files with "Win XP" using [fs-driver]("http://www.fs-driver.org/") (probably it's not the best idea but is my life, ok?? :oops:). Well, for a reason that I haven't discovered yet, some inodes breaks down and I lost one of the directories in this disk (using fsck resolved the problem, but I didn't recover the DIR). Simplifying my life, I endorsed the rest of files and format again using GParted. As the fs-driver did not work (says to me that the disk need the format, problem that appears with ext3 disks) restart in linux to check the filesystem of disk and I discovered some incongruities:

GParted says: 
**ext2** , **free space: 36.63 GiB**, **used space: 647.224 MiB**

Properties:(right click over disk in desktop) says:
**ext3** , **free space: 34.8 GiB**, **used space: 1.9 GiB**

df-h command says:
[B]                    size  used  free
/dev/sda1              37G   48M   35G   1% /media/Respaldo

[/B]

screenshoot: (I have 8.10 - Intrepid Ibex ubuntu in Spanish)
[IMG]http://molavec.vndv.com/imagenes/disk.png[/IMG]

So, my questions are:

1.-Why in properties window appars ext3? is a bug?
2.-which program is more reliable to check the size of used y free space in the disk?? Personally, I believe  to "df" command but why GParted show me this values??
3.- How much space disk consume the EXT2 filesystem immediately after format a disk?

Optional: 3.- Some idea for why de fs-driver (in windows) don't reconigze the this after the format disk although de filesystem is the same.

---

### Post by molavec on 2009-09-23
Respect to my thirth question

"3.- Some idea for why de fs-driver (in windows) don't reconigze the this after the format disk although de filesystem is the same."

In fs-driver page I found [this]("http://www.fs-driver.org/troubleshoot.html"). Run the executable file show me this message:

[IMG]http://img148.imageshack.us/img148/871/mountdiag.jpg[/IMG]

So this I can get a solution to my problem but no answer my questions 1 and 2.

So, I will wait for your help.

---

