---
title: "Bash Loop - Server Backup Script"
date: 2012-01-06
forum: General Help
---

### Post by sibleytr on 2012-01-06
Just giving back to the community:

We are in the process of coverting a number of our file servers from the Windows platform to the Linux Ubuntu Samba platform. The primary target being our File Back Up servers. Along with the conversion process is the conversion of our backup scripts from Windows Command Line to Ubuntu Bash.

So as us noobs stumble around trying to figure out how to do in Ubuntu what we used to do in Windows, I hope this gives you an example to build on. The following code is used on our Disaster Recovery Server, which is basically an offsite backup server for our onsite backup server. In this particular process, the data is overlaid after each backup.

```

#! /bin/bash
#
### OLFS - Off Line File Server - Bash Back Up
#
### Local File Variables
#  iniFl - INI space delimited file location
#  pwdPth - Password file location
#
   iniFl=/mnt/rsyncMe/data.ini
   pwdPth=/mnt/domSvs/.pword
#
### Loop olfs08.ini file
#  olfs - OLFS file server
#  evol - External Volume Number
#  sv - Server Name (Folder)
#  sd2tb - Target backup drives
#
while read olfs evol sv sd2tb
 do
  srcPth=//$olfs/$evol/$sv
  mntPth=//mnt/domSvs/$olfs/$evol/$sv
  trgPth=/mnt/extHds/$sd2tb/$sv
#
  mkdir -p $mntPth
  mkdir -p $trgPth
#
  mount -t cifs $srcPth $mntPth -o credentials=$pwdPth
  rsync -arvz --progress $mntPth/* $trgPth
  umount $mntPth
  done < $iniFl
#
### End

```

Because learning how to work with reading files is really what makes working with scripting fun I thought I would go into the while loop with a bit more detail - you can't be a noob forever.


As a primer, keep in mind that the "data.ini" file is a standard text file that has four data sets, each separated by a space. The example contents of are:
```

olfs08 evol1 dalfps sdc2tb
olfs08 evol2 denfps sdc2tb
olfs08 evol3 shrfps sdc2tb

```

Looking at the WHILE loop...
```

while read olfs evol sv sd2tb
 do
  srcPth=//$olfs/$evol/$sv
  mntPth=//mnt/tnpinc/$olfs/$evol/$sv
  trgPth=/mnt/extHds/$sd2tb/$sv

```
The WHILE loop reads the first line of the "data.ini" file and assigns each of the line data elements to a string variable. Therefore, the first data set would be

olfs = **olfs08** - the server that has the data
evol = **evol1** - the volume residing on the server
sv = **dalfps** - the folder residing within the volume (named after server)
sd2tb = **sdc2tb** - the volume name in which the data will be backed up to

Given the four parts of data we can create our
**srcPth** - Source Path - Where the data resides
**mntPth** - Mount Path - Where the server will mount to obtain the data
**trgPth** - Target Path - Where the data will be backed up to


In the event the folders need to be created...
```

  mkdir -p $mntPth
  mkdir -p $trgPth

```

Then we just mount, backup using rsync, and umount when complete...
```

  mount -t cifs $srcPth $mntPth -o credentials=$pwdPth
   rsync -arvz --progress $mntPth/* $trgPth
  umount $mntPth

```

This handy piece of code completes the WHILE statement, but also tells the WHILE statement where the external file is
```

done < $iniFl

```


The future Bash script will need to create backup folders based on YYYYMMDD to hold incremental data.

Hope this helps someone out there.

---

