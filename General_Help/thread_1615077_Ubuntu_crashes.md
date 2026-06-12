---
title: "Ubuntu crashes"
date: 2010-11-06
forum: General Help
---

### Post by shockron22 on 2010-11-06
Ok guys i have ubuntu installed inside windows 7 and i got a message saying that there was a new version of ubuntu and if i wanted to install so i did and now when i try to boot to ubuntu all i get is the grub screen and i need to get some of my flies off the ubuntu half onto the windows one. How do i do that or can ubuntu be fixed without eraseing my files.  
 Thanks

---

### Post by Mark Phelps on 2010-11-06
Unfortunately, the Release Notes for 10.10 indicated that attempting to upgrade Wubi from 10.04 to 10.10 fails -- and it looks like you got caught in that.  It's generally NOT a good idea to upgrade Wubi installations anyway -- as they were originally intented as a simple vehicle for trying out Ubuntu, and not intended to be used long-term.

I don't use Wubi, so I don't have a fix -- but others do and perhaps one of them can provide you a link to some items you can patch.  Sorry

---

### Post by shockron22 on 2010-11-06
damn, I have file that i need on there. 

Thanks man

---

### Post by kuvanito on 2010-11-06
run ubuntu from the cd and save all the info you want from that drive,then wipe it out with a new installation of ubuntu,forget about dual boot,PLEASE!
either run ubuntu or just stay in windows or GET TWO SEPARATES DRIVES!

---

### Post by bcbc on 2010-11-06
the program [ext2read]("http://ext2read.blogspot.com/") can give you readonly access to your wubi install from windows - just point it at c:\ubuntu\disks\root.disk.

For fixing the install - [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

To migrate a wubi install to a full partition install see this [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by P4man on 2010-11-06
> **kuvanito said:**
> run ubuntu from the cd and save all the info you want from that drive,then wipe it out with a new installation of ubuntu,forget about dual boot,PLEASE!
either run ubuntu or just stay in windows or GET TWO SEPARATES DRIVES!

There is absolutely no need for 2 drives. Partitioning works just fine, but I do concur with Mark that wubi is not a good long term solution. Time to install ubuntu on its own partition after recovering your files.

---

### Post by shockron22 on 2010-11-06
ok guys i got to my files but one of the moast important ones says accsess denied and that i dont have permission to copy it  im booting from a live cd and i mounted the wubi directory and stuff but i cant get past this   permission thing    any ideas??

---

### Post by shockron22 on 2010-11-06
its a 4.3 gig  file also if that helps any

---

### Post by shockron22 on 2010-11-06
> **kuvanito said:**
> run ubuntu from the cd and save all the info you want from that drive,then wipe it out with a new installation of ubuntu,forget about dual boot,PLEASE!
either run ubuntu or just stay in windows or GET TWO SEPARATES DRIVES!
ubuntu is my main operateing system but windows can do some things ubuntu cant like run some programs that are nice to have.

---

### Post by P4man on 2010-11-06
start nautilus with root permissions:

```
gksudo nautilus
```

Use that to copy your files. And even though its already bricked, be very careful what you do.

---

### Post by shockron22 on 2010-11-06
> **P4man said:**
> start nautilus with root permissions:

```
gksudo nautilus
```

Use that to copy your files. And even though its already bricked, be very careful what you do.
THANKS!!!  it worked like a charm got all my files right and now i can re-install everything

---

### Post by shockron22 on 2010-11-06
oh how do you mount an ipod touch with the cmd???

---

### Post by shockron22 on 2010-11-06
I lost my flash drive and need to use my ipod but it doesnt auto recognise so i need to do it from the cmd or somethin else

---

