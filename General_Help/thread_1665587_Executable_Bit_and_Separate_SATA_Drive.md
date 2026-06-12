---
title: "Executable Bit and Separate SATA Drive"
date: 2011-01-12
forum: General Help
---

### Post by Rsjc741 on 2011-01-12
I'm having a bit of a problem enabling any sort of permissions for my 1TB SATA HDD on /dev/sda1. Using Nautilus and wine, I'm trying to play games already pre-installed on my Windows 7 partition. When ever I right-click>permissions>Enable execution, it reverses the changes.
I don't know if this is relevant, but id rather not copy anything on to my /dev/sdb2/ partition because its about 1/10th the size of sda1 (142GB free to be exact)

Is their any way to make a permanent change?

I don't really mind if it's a solution in the terminal... So long as it doesn't mess up my ability to boot Windows 7.

---

### Post by Spyderkid on 2011-01-12
run this 
```

sudo chmod FILENAME

```

---

### Post by Rsjc741 on 2011-01-12
I need a operand after the filename.
should i just do chmod (filename) -v?

*edit:

Scratch that, I did sudo chmod u=rwx *.exe -v
(* indicates the filename in this case, not a wildcard)
My mode is now 700.
Since all 5 hyphens after rwx are well.. hyphens, does this mean I still have no r/w/x permissions?

---

### Post by WorMzy on 2011-01-12
Just FYI: you should avoid running things directly from NTFS partitions. Due to limitations with the ntfs-3g driver it will have a negative effect on the performance of the application in question, and may even cause the application to crash. This isn't so much of a problem for small applications, but things like games or the adobe suite will be affected by it. Installing the application to a partition formatted as a native filesystem (e.g. ext4) will provide a much better experience.

Still, if you want to try running things from the NTFS partition, then check out this tutorial: [[COLOR="DarkGreen"]HOWTO: Mount NTFS partitions with specific ownership/permissions[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1604251")

---

