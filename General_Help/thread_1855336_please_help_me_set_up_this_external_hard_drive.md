---
title: "please help me set up this external hard drive"
date: 2011-10-06
forum: General Help
---

### Post by bradlees on 2011-10-06
cheers all,

I recently purchased a wd passport 320gb usb hard drive. I currently primarily use ubuntu, but also have windows 7 on my laptop. I would like to use the external drive to do windows back ups and to store media, pictures and music, on so I can swap my library between machines. 

I need a little help on how to set this thing up so it can be used by both os's, if this is even possible. It works on windows, but says it is a read only device while using ubuntu.

What to do?

thanks

---

### Post by wildmanne39 on 2011-10-06
Hi, you can format it to ntfs that way windows and ubuntu can read it.

I do not know about window permissions, hopefully that will be fixed by reformatting.
Thank you

---

### Post by bradlees on 2011-10-06
should i format it using windows or ubuntu? Also i would like to keep the restore partition that is on it, it has a program that is installed on it, could i keep this and format a partition as well?

---

### Post by amjjawad on 2011-10-06
> **bradlees said:**
> I need a little help on how to set this thing up so it can be used by both os's, if this is even possible. It works on windows, but says it is a read only device while using ubuntu.

Linux, by default, can Read/Write from/to NTFS Partitions.
Perhaps it's write protected so check that on Windows.

---

### Post by amjjawad on 2011-10-06
> **bradlees said:**
> should i format it using windows or ubuntu? 

That shouldn't matter with External HDD which will be used as backup.



> Also i would like to keep the restore partition that is on it, it has a  program that is installed on it, could i keep this and format a  partition as well?
How many partitions do you have on it?

---

### Post by wildmanne39 on 2011-10-06
Hi, you will need to resize your partition to get the data that is in that partition because reformatting will wipe the data out.

I guess you can use windows to reformat the drive but it might cause the permission issue again, I am not sure about that, here is some links on partitions.
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Make backups of your important data before you resize and reformat your drive.

Resizing partitions can take a long time so be patient.
Thank you

---

