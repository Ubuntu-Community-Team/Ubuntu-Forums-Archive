---
title: "need help installing stuff"
date: 2009-07-07
forum: General Help
---

### Post by starcraftmaster on 2009-07-07
hey guys 
am trying to install DOOM 3
but it wont let me , what i do is i open the .run file and then tell it to open with SH
it opens and when i go to the part of where i want to install it
i change it to D:/program files/doom3
and then i go OK and it says: you don't have permisson to write to D:/programs files/doom3

so i right clicked in the D:/ drive and i tell it to put permission on read and write but it goes back to blank and wont let me choose what i want
also i need to put it on D: drive because the ubuntu drive does not how much room left:mad:

so how do i get full admin rights ?
and how do i set permission ?

also i tried terminal
i did sudo sh doom3-linux-1.3.1.1304.x86.run
same problom still( i had to type my password)

---

### Post by danwood76 on 2009-07-07
When you say D: what do you mean?
In ubuntu you dont have drive letters but block numbers and mount points.

You will not be able to install a linux app to a windows partition as the permissions will not be correct and it wont be able to run.

---

### Post by starcraftmaster on 2009-07-07
> **danwood76 said:**
> When you say D: what do you mean?
In ubuntu you dont have drive letters but block numbers and mount points.

You will not be able to install a linux app to a windows partition as the permissions will not be correct and it wont be able to run.

D: is a drive
and its not a windows partition
but it has been formatted in fat32

so you cant install stuff on different drives?
then thats quite annoying
they better fix that

---

### Post by XCan on 2009-07-07
No, what danwood meant to ask is how you managed to get the mountpath D:/ in Ubuntu. That seems like an illegal path for me since it doesn't even start with /. Normally they would end up in /media/<drivename>. 

You sure can install onto other drives. When you've found the correct path you can change owner of the whole drive/dir using 

chown username:username -R <your.path>

---

### Post by danwood76 on 2009-07-07
You wont be able to launch a linux app from fat32 I doubt.
This is because most apps require certain permissions within the program structure.

Try installing to a linux drive and see how you fair.

---

### Post by starcraftmaster on 2009-07-07
> **XCan said:**
> No, what danwood meant to ask is how you managed to get the mountpath D:/ in Ubuntu. That seems like an illegal path for me since it doesn't even start with /. Normally they would end up in /media/<drivename>. 

You sure can install onto other drives. When you've found the correct path you can change owner of the whole drive/dir using 

chown username:username -R <your.path>

oh
i still use the windows sytle
in ubuntu its 10.7 gb media
but in the doom 3 install i type D:/programs files/doom 3
so am i meant to do 10.7 gb media:/programs files/doom 3 ?
or some thing else?

---

### Post by danwood76 on 2009-07-07
you need to work out what the mountpoint of the drive is.
This is usually quite simple, navigate to the drive and click up directory. This should drop you into the media folder where the drive will be. Make sure its the correct one and then the path will be:
```

/media/MOUNTPOINT/Programs/.....

```
But I doubt it will work from fat32 as you cannot set permissions, though I have never tried.

---

### Post by CatKiller on 2009-07-07
> **starcraftmaster said:**
> so you cant install stuff on different drives?
then thats quite annoying
they better fix that

You might find [this page]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") to be useful reading.

Just because Linux isn't limited by using drive letters, that doesn't mean you can't use multiple partitions however you please. You just need to know where you've mounted them.

In your case, you'd probably find it much more straightforward to just make your Linux partition larger using GParted on the install cd by reclaiming some free space from another partition that has plenty, and then installing any Linux programs to their default location.

Having said that, I don't think that the limitations of the FAT filesystem (of which there are many) will be a problem in this case. The lack of support for UNIX permissions means that FAT is right out for Home folders or some of the more sensitive parts of some of the fundamental secure components, but the Doom 3 files are just data and I shouldn't imagine that they would include any unsafe filenames. Certainly my UT install, which was temporarily on a FAT filesystem, worked fine. I'd symlinked the partition's mountpoint to the default install location for UT, though.

---

