---
title: "DVD Recovery Utilities"
date: 2010-10-11
forum: General Help
---

### Post by houseisland on 2010-10-11
Hi,

I wonder if anyone knows of any DVD recovery utilities/command line options that would work with Lucid.

I was given a DVD that does not seem to have been burned properly; it appears not to have been closed.  

The Windows utilities, ISOBuster and CDRoller, can find the .VOB files on the disk even though Windows cannot mount the volume as there is no recognized file system.  However, the recovery options in these two utilities are not available in unregistered installations of the software.  And yes, I could deal with this minor obstacle very easily, but I generally prefer not to go down than road.  ;)

The DVD will not mount in Lucid either.

Any suggestions?

Thanks.

:)

---

### Post by todak on 2010-10-11
There is a utility available in the repositories called ***dares***. A graphical version call ***dares-qt*** is also available. It can read the discs even thought they cannot be mounted.

---

### Post by houseisland on 2010-10-11
> **todak said:**
> There is a utility available in the repositories called ***dares***. A graphical version call ***dares-qt*** is also available. It can read the discs even thought they cannot be mounted.

Hi,

Thanks.  Either it does not work or I do not know what I am doing.  The later is a distinct possibility.

I get a variety of errors trying different things but most commonly:

dares 0.6.5 started at Mon Oct 11 20:22:10 2010
opening image /dev/sr0: ok
Could not load file magic database file 'magic', using default database
, 0: Warning: using regular magic file `/etc/magic'
block        0 (0 files)
block 0: read(): 5 (Input/output error)

error: scanned 0 2k blocks, found 0 files

---

### Post by prkos on 2010-11-06
Thanx for the tip

Here's my experience with a DVD that wouldn't mount: 

On one computer dares gave errors (10.4) when trying to rescue a DVD, so I used gddrescue to create a regenerated iso image. I burnt the image on a new disc but it also wouldn't mount. 

Then I used dares on a different computer (9.10) to read the image from gddrescue and it quickly found the files. I saved all, this took some time and I got a bunch of .bin files for my photos.  

To me the most important files to rescue were photos in jpg, so I used the batch GIMP plugin to rename them to jpg (GIMP would open even the .bin files without problems).

---

### Post by alphaamanitin on 2010-11-06
You could try to make an iso of the DVD with the dd command.  Then use an archive manager to open it.  I think.  I know WinRAR will extract .iso files.  I think it is a simple solution that is worth a shot.  

AlphaA

---

