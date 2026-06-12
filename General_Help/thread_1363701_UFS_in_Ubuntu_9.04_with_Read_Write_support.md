---
title: "UFS in Ubuntu 9.04 with Read Write support?"
date: 2009-12-24
forum: General Help
---

### Post by mac666 on 2009-12-24
Hey
Im trying to mount my UFS disk from freeNAS (freeBSD), on my Ubuntu machine but i cant.

I get the regular error message that everybody gets at their first attempt. 

My question is basic, is it possible to mount an UFS drive on Ubuntu 9.04 with the latest kernel and support read / write?

Since my NAS died and i cant read it any other way, and i cant convert the drive, how should i do if i need to read the data? 
I have 3 drives @ 1,5 TB that needs to be saved... :(

EDIT: I have UFS as Module in the config file, so i did sudo modprobe ufs without problems, rebooted and tried to mount but still wouldnt do it. This is that the mount command givs me if i give it dsmesg:
ufs was compiled with read-only support, can't be mounted as read-write

---

### Post by mac666 on 2009-12-26
Bump?

---

### Post by Curtis.Everingham on 2010-01-14
I'm trying to mount UFS filesystems as well, only in 9.10. any help with this would be greatly appreciated.

---

### Post by Corgana on 2010-01-29
Bump again.

Somebody has to know, UFS seems to be a popular filesystem..

---

### Post by jeppebundsgaard on 2010-02-04
Did you install ufsutils?

```
sudo apt-get install ufsutils  
```

---

### Post by mac666 on 2010-02-04
yepp... That wont do it

---

### Post by davec64 on 2010-02-04
Do you have a 2nd PC/laptop?

You could download and boot FreeNAS from a CD with the UFS Drive attached (removing your Desktop drive) and then use the 2nd PC/Laptop to copy off the files.

It's awhile since I ran FreeNAS but if you can boot a FreeNAS installation from the CD you always use to be able to create a floppy from it for booting.

Not a solution to your problem but a possible "get out of jail"!  

Best of luck :)

---

### Post by Corgana on 2010-02-04
> **davec64 said:**
> Do you have a 2nd PC/laptop?

You could download and boot FreeNAS from a CD with the UFS Drive attached (removing your Desktop drive) and then use the 2nd PC/Laptop to copy off the files.

It's awhile since I ran FreeNAS but if you can boot a FreeNAS installation from the CD you always use to be able to create a floppy from it for booting.

Not a solution to your problem but a possible "get out of jail"!  

Best of luck :)

That's exactly what I just did, unfortunately I had a terabyte of data, So it took 3 External hdds. I'm curious as to why support for this dosen't exist yet, while support for ntfs is nearly flawless. Does anyone know?

---

### Post by davec64 on 2010-02-04
I suppose its down to the fact the UFS comes from BSD whereas NTFS from MS and its simply down to the number of users that want to access it.
If there wre more users wanting acces to UFS I'm sure somebody would then try to integrate it.

As FreeNAS is such a good thing, it's a shame it doesn't support Ext/2/3/4.

---

### Post by Corgana on 2010-02-04
> **davec64 said:**
> I suppose its down to the fact the UFS comes from BSD whereas NTFS from MS and its simply down to the number of users that want to access it.
If there wre more users wanting acces to UFS I'm sure somebody would then try to integrate it.

As FreeNAS is such a good thing, it's a shame it doesn't support Ext/2/3/4.

IIRC, it supports ext2. (At least read-only)

---

