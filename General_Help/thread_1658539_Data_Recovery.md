---
title: "Data Recovery"
date: 2011-01-02
forum: General Help
---

### Post by Taters343 on 2011-01-02
Earlier I meant to format my flash drive, but I selected the wrong thing and accidentally started formatting my external hard drive (I know, I'm an idiot). I noticed right away and hit cancel, but now the hard drive has a new name and no files in it, but the properties still says it has all of the data on it.

I downloaded a program called extundelete, but before I use it I want to make sure it is the right thing to use. Any help getting my files back would be very appreciated.

---

### Post by Joe of loath on 2011-01-02
Photorec should be able to do it.

---

### Post by Bitrate on 2011-01-02
Download a system rescue cd, boot it and run Testdisk.

A good disk to try is SystemRescueCD ([http://www.sysresccd.org](http://www.sysresccd.org)).

---

### Post by fabricator4 on 2011-01-02
Provided you don't _write_ to your damaged partition extundelete won't actually harm anything - one of the first rules of data recovery is to write the recovered files to another drive or partition.

I'm not sure undelete is going to find much as I have no experience with ext partition file recovery so I'm interested to see what others say.

Chris

---

### Post by Taters343 on 2011-01-08
I tried using Testdisk, but it didn't even recognise that the hard drive is partitioned.

Now I'm trying extundelete, I'm in the directory in which I would like to restore the files and I typed "sudo extundelete --restore-all /dev/sdg1" To which it told me, "extundelete: failed to read-only open device "/dev/sdg1": Error code 2133571347"

Does anybody know what I should do from here?

---

### Post by aysiu on 2011-01-08
Since you have *testdisk* already installed, run the command ```
sudo photorec
```

---

### Post by Taters343 on 2011-01-08
> **aysiu said:**
> Since you have *testdisk* already installed, run the command ```
sudo photorec
```

I did that. It sees both hard drives, but not both partitions on the one I want to restore.

---

### Post by aysiu on 2011-01-08
> **Taters343 said:**
> I did that. It sees both hard drives, but not both partitions on the one I want to restore.
Why does it have to see the partitions? It does a low-level scan, so you can just run it on the whole drive.

---

### Post by Taters343 on 2011-01-08
> **aysiu said:**
> Why does it have to see the partitions? It does a low-level scan, so you can just run it on the whole drive.


Ok.

---

### Post by Taters343 on 2011-01-08
> Please select the partition table type, press Enter when done.
[Intel  ]  Intel/PC partition
[EFI GPT]  EFI GPT partition map (Mac i386, some x86_64...)
[Mac    ]  Apple partition map
[None   ]  Non partitioned media
[Sun    ]  Sun Solaris partition
[XBox   ]  XBox partition
[Return ]  Return to disk selectionI do not know what to say to this.

---

### Post by aysiu on 2011-01-08
Select *Intel*

---

### Post by Taters343 on 2011-01-08
Stuff is being recovered. So far a lot of the videos file seem to be really messed up. Looks like it took one big video file and split it into dozens of smaller ones. If I'm remembering correctly, the original file was an .iso, so that could have caused it I suppose.

---

### Post by Taters343 on 2011-01-09
This has been completely useless. Over 500 GB of data recovered, but nothing usable. There are still a few hours left on the scan, but I doubt any good will come of them. It is probably just the data that is not recoverable, but I'd still like to try extundelete if anyone knows how to get past that error message.

---

