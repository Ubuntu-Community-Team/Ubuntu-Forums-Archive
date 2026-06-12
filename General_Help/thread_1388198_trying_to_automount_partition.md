---
title: "trying to automount partition?"
date: 2010-01-22
forum: General Help
---

### Post by pokemoncatdog on 2010-01-22
I know how to automount ntfs, what I don't know is how to automount a 2nd ext4 partition. I know I can use  [B]"sudo gedit /etc/fstab"

I tryed : 
sudo mkdr /media/windows 
sudo gedit /etc/fstab[/B]
[B]
 Then added
[/B] [B]/dev/sda1 /media/windows ext4  users,defaults,umask=000 0 0\
[/B][B] 
 Restart pc and did not work.[/B]


**What am I doing wrong?**  Also how can I read and write to and form the root of the partition with out opening it as root? 
This is not the partition I have ubuntu installed on, this is a 2nd partition.


[B]SEE THE ATTACHED SCREENSHOT!
[/B]

---

### Post by JackRock on 2010-01-22
I solved this problem by installing the Disk Manager.  Search for "pysdm" in Synaptic.

---

### Post by n0dix on 2010-01-22
Try this in your fstab:
```
/dev/sda1 /media/windows ext4 defaults 0 1
```

---

### Post by bodhi.zazen on 2010-01-22
See this link : [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

ext4 partitions do not use umask

---

