---
title: "OOo4kids (Open Office for Kids) installation help?"
date: 2010-06-06
forum: General Help
---

### Post by windfix on 2010-06-06
The OOo4kids project seems pretty cool for K-12 educators.  I got the Windows version installed in no time.  The Ubuntu version, however, I can not install.  It provides a .tar.gz file and a .md5 file; inside the .tar.gz are a bunch of .debs - which I am used to using archive manager to unpack.  However, each of them seems to be dependent on another one of them and I can not get them installed.  Nor are there directions.

Can anyone tell me how to install this?

---

### Post by stderr on 2010-06-06
Not sure, but I'd assume it should work if you pass them all to dpkg simultaneously:

```
sudo dpkg -i pkg1.deb pkg2.deb pkg3.deb
```

edit: Scrap that, it looks like you install package "ooo4kids-ure". Everything seems to ultimately depend on that.

---

### Post by windfix on 2010-06-06
Thanks. I did install ooo4kids-ure_1.5.0_386.deb

Next, I tried ooo4kids0.9.5_i386.deb, and I get "Error: Dependency is not satisfiable: OOo4Kids-ure"

---

### Post by stderr on 2010-06-06
Right, I've just tried it myself, so this is what you do:

```
cd the_dir_you_unpacked_the_tar_gz_to/en-US/DEBs/
sudo dpkg -i *.deb

```

The application binaries are placed in:

```
cd /opt/ooo4kids0.9.5/program
ace@ace1:/opt/ooo4kids0.9.5/program$ ls -l
total 256
-r--r--r-- 1 root root 64839 2010-05-28 17:46 about.png
-r--r--r-- 1 root root   333 2010-05-28 17:46 bootstraprc
-r--r--r-- 1 root root   986 2010-05-28 17:46 fundamentalrc
-r--r--r-- 1 root root 94435 2010-05-28 17:46 intro.png
-r--r--r-- 1 root root    50 2010-05-28 17:46 redirectrc
drwxr-xr-x 2 root root  4096 2010-06-07 02:35 resource
[B]-r-xr-xr-x 1 root root    61 2010-05-28 17:50 scalc
-r-xr-xr-x 1 root root    61 2010-05-28 17:47 sdraw[/B]
-r--r--r-- 1 root root    56 2010-05-28 17:46 setuprc
[B]-r-xr-xr-x 1 root root    64 2010-05-28 17:46 simpress
-r-xr-xr-x 1 root root    61 2010-05-28 17:50 smath[/B]
**-r-xr-xr-x 1 root root  3858 2010-05-28 17:46 soffice**
-r-xr-xr-x 1 root root  9672 2010-05-28 17:46 soffice.bin
-r--r--r-- 1 root root   156 2010-05-28 17:46 sofficerc
-r-xr-xr-x 1 root root  2539 2010-05-28 17:46 spadmin
**-r-xr-xr-x 1 root root    63 2010-05-28 17:47 swriter**
-r-xr-xr-x 1 root root  1842 2010-05-28 17:46 unoinfo
-r-xr-xr-x 1 root root  2654 2010-05-28 17:46 unopkg
-r-xr-xr-x 1 root root  9672 2010-05-28 17:46 unopkg.bin
-r--r--r-- 1 root root   375 2010-05-28 17:46 versionrc

```

---

### Post by bodhi.zazen on 2010-06-06
> **windfix said:**
> Thanks. I did install ooo4kids-ure_1.5.0_386.deb

Next, I tried ooo4kids0.9.5_i386.deb, and I get "Error: Dependency is not satisfiable: OOo4Kids-ure"

In a terminal try ```
sudo apt-get install -f
```

---

### Post by windfix on 2010-06-06
Thanks, that totally worked!  Man, they could have made that easier. Hopefully when it's out of beta.

For anyone else trying this, once it's installed - you can create a launcher (right click on desktop or elsewhere) and point it to /opt/ooo4kids0.9.5/program/soffice.bin

You can also change its icon to one of the .png files there to make it look nicer.

---

### Post by benbois on 2010-06-07
test reply..

---

### Post by ericb2 on 2010-06-07
Hi,

FYI, I created a script for the installation, that you can find at :
[http://eric.bachard.free.fr/OOo4Kids/patches/May_2010/31st_may/InstallOOo4kids4.sh](http://eric.bachard.free.fr/OOo4Kids/patches/May_2010/31st_may/InstallOOo4kids4.sh)

You must run it as root (or using sudo), and then, you should be able to 

- install OOo4Kids
- uninstall OOo4Kids

Of course, this script can be improved, and any help is welcome :-)

Thanks in advance

---

### Post by benbois on 2010-06-07
Thank you Eric!

I tested your script with success on Ubuntu 9.04 / 64b

Cheers,
--
Ben

---

