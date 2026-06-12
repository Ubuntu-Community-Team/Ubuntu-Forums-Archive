---
title: "Conky Disk Usage Help"
date: 2010-01-17
forum: General Help
---

### Post by distortedecho on 2010-01-17
Hi,

I have the default Conky script, but want it to also monitor my secondary drive.

How do I do this, please?

Thanks.

---

### Post by VCoolio on 2010-01-17
There are several options:

fs_bar - Bar that shows how much space is used
fs_free - Free space on a file system
fs_free_perc - Free percentage of space
fs_size - File system size
fs_used - File system used space

Use one or more of the above followed by the path to the folder / partition / disk you want (probably starting with /media), eg. 
${color}Disk: ${fs_used /path/disk} of ${fs_size /path/disk} used

More options to be found [here](http://conky.sourceforge.net/docs.html).

---

### Post by distortedecho on 2010-01-17
Thanks, I'll give it a go, and if I get stuck I'll let you know. :)

---

### Post by distortedecho on 2010-01-18
OK I have:

${color grey}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar 6 /}
${color grey}Storage:
 /Storage $color${fs_used /dev/sda2}/${fs_size /dev/sda2} ${fs_bar 6 /dev/sda2}

But, my output for Storage is:

284KiB/1.23GiB

What the?

---

### Post by VCoolio on 2010-01-18
You need the mount point, not the device. Use the /media/whatever path or whereever you mounted /dev/sda2.

---

### Post by distortedecho on 2010-01-18
How can I find out the mount path?

---

### Post by VCoolio on 2010-01-18
in terminal: mount

or in this case for convenience: mount | grep sda2

---

### Post by distortedecho on 2010-01-23
Perfect - it worked!

Thanks alot guys!

---

### Post by pw_f100_220 on 2010-01-24
Is there a way to have the entire hard drive (multiple partitions mounted at different points) displayed as a whole?  I could display them separate, but i just want one.

one drive with different partitions mounted at /boot, /, and /home

---

### Post by I'mGeorge on 2010-10-31
> **pw_f100_220 said:**
> Is there a way to have the entire hard drive (multiple partitions mounted at different points) displayed as a whole?  I could display them separate, but i just want one.

one drive with different partitions mounted at /boot, /, and /home

Well I don't know if my reply came a little bit too late but because I've stumbled on the same thing, I've wrote the following lines for conky, so it will display the characteristics of my NTFS partitions as a whole. It should be enough to change mnt from the awk command with the folder where you have your partitions mounted.

```

${color grey}NTFS HDD ${color 115199} ${exec df -H|awk '/mnt/ {avail += $4; size += $2; used += $3} END {print int(avail*100/size)"%""                   "used"GiB"" " "of" " "size"GiB"}'}
${color}${execbar exec df -H|awk '/mnt/ {avail += $4; size += $2} END {print int(avail*100/size)}'}

```

eventually you should end up with something like [this]("http://www.linuxquestions.org/questions/attachment.php?attachmentid=5036&d=1288464765")

---

