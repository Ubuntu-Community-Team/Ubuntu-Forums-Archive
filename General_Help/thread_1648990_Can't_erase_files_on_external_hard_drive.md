---
title: "Can't erase files on external hard drive"
date: 2010-12-19
forum: General Help
---

### Post by jereece on 2010-12-19
I bought a new 2.5 inch SATA laptop hard drive and mounted it in an external enclosure for use as an external backup drive.  I had a whale of a time getting it formatted ([ref post]("http://ubuntuforums.org/showthread.php?t=1648376")), but finally did by putting the bare drive into a laptop and used Ubuntu to partition and format as part of installing.  Then I remounted the bare drive back into the enclosure and sure enough now I can now see the drive.  

So now I want to erase the files from the backup drive.  Problem is, Ubuntu won't let me delete or add any files.  In Nautlis, if I select the files and "right click", Move to Trash is grayed out.  If I press the delete button, nothing happens.  If I try to copy a new file to the backup drive it says "permission denied".  If I go into the Properties .> Permissions for the drive everything is grayed out so I can't change the permission.  It also says "You are not the owner so you cannot change permissions".  

Holy cow I never dreamed such a simple thing would be so difficult.  Does anyone know what I need to do here?

I appreciate the help.

Jim

---

### Post by desnaike on 2010-12-19
I usually run nautilus as root (sudo nautilus) and change my external drives permissions from there.

---

### Post by Irony on 2010-12-19
> **desnaike said:**
> I usually run nautilus as root (sudo nautilus) and change my external drives permissions from there.
Should be;

```
gksudo nautilus
```

---

### Post by techunit on 2010-12-19
To use an external drive? Actually I bet you formated it in such a way that the Fstab isn't recognizing it. Fstab is one of those things I won't touch so I don't know to much about it. Anyway, hopefully someone will be able to help him with the problems. My best regards.

---

### Post by jereece on 2010-12-19
Okay I finally went back into Gparted and unmounted the drive and now it will let me reformat.  

Next question, what type of file system should I use for a backup drive if I want to be able to access it from Linux or Windows?

Thanks,
Jim

---

### Post by dcstar on 2010-12-20
> **jereece said:**
>   
Next question, what type of file system should I use for a backup drive if I want to be able to access it from Linux or Windows?


You cannot properly backup all Linux files to non-Linux filesystems, so you should use a Linux filesystem like EXT3 and install the Windows software to read it.

You can try NTFS but there are no guarantees that it will back up you system correctly.

---

### Post by jereece on 2010-12-20
I am only backing up files (e.g. documents, pictures, video, etc.) not system files.

---

### Post by Irony on 2010-12-23
ntfs will work fine, fat will but I think it doesn't handle files over 4GB in size.

---

