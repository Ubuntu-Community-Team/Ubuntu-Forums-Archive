---
title: "Installing hdparm from source / Having issues with DiskTRIM"
date: 2010-05-22
forum: General Help
---

### Post by ShakeyJake on 2010-05-22
Hey guys,

I know this isn't exactly a DiskTRIM forum but the project appears to be defunct. Hopefully someone here is using it, or have you found another way to trim your OCZ SSD?

I have a Vertex Turbo which has gone from 240MB/s when I just got it to under 70 now. It's an ext 4 system and I'm running a compatible kernel (2.6.32.22).

I simply cannot get the newer version of hdparm to install. I got the .tar for 9.28 and I believe it is installed, it appears in /home/Jack/hdparm-9.28. Is that the correct place? There is no 'hdparm' folder. Synaptic reckons I have 9.15 or something installed still. 

Either way, when I engage DiskTRIM it doesn't do anything. Has anyone got an easy way of making sure I have the right hdparm and then getting trim to work on my SSD? This system is getting quite slow now and it's starting to bug me,

Thanks for anything,
Jack

---

### Post by 98cwitr on 2010-05-22
Just posted instruction on another site...

[http://forums.clubrsx.com/showthread.php?p=33429489#post33429489](http://forums.clubrsx.com/showthread.php?p=33429489#post33429489)


I was struggling with the same thing about 2 minutes ago :)

[http://ubuntuforums.org/showthread.php?t=1488123](http://ubuntuforums.org/showthread.php?t=1488123)

MY SSD is a Mushkin MKNSSDCL60GB
before:
[img]http://img.photobucket.com/albums/v673/98cwitr/Screenshot-60GBSolid-StateDiskATAMu.png?t=1274586547[/img]


after:
[IMG]http://img.photobucket.com/albums/v673/98cwitr/Screenshot-60GBSolid-StateDiskAT-2.png[/IMG]

---

### Post by ShakeyJake on 2010-05-23
You sir, are a helpful genius!

Now that it's done (and it's working) I am only getting read speeds of ~100MB/sec according to hdparm. 

I know fine well my disk is capable of 240-270MB/sec as I benched it when I first got it, any ideas why this is? I have tried running TRIM several times now.


Edit: You forgot to add the '--commit' option in the last command. :)

---

### Post by 98cwitr on 2010-05-24
> **ShakeyJake said:**
> You sir, are a helpful genius!

Now that it's done (and it's working) I am only getting read speeds of ~100MB/sec according to hdparm. 

I know fine well my disk is capable of 240-270MB/sec as I benched it when I first got it, any ideas why this is? I have tried running TRIM several times now.


Edit: You forgot to add the '--commit' option in the last command. :)

what does the --commit command do? I didn't run that :)

Well the only thing I could think of is that the MLC is degrading...but that would be a really really fast degrade time even for an MLC drive

read this: [http://www.anandtech.com/print/2738](http://www.anandtech.com/print/2738)

---

### Post by ariel on 2010-05-24
> **98cwitr said:**
> what does the --commit command do? I didn't run that :)

Well the only thing I could think of is that the MLC is degrading...but that would be a really really fast degrade time even for an MLC drive

read this: [http://www.anandtech.com/print/2738](http://www.anandtech.com/print/2738)


It doesn't work in Intel X25-M.  Hdparm 9.28 / wiper.sh as well as wiper-intel.sh still give the FAILED INPUT/OUTPUT errors.

---

### Post by 98cwitr on 2010-05-25
what's the error(s) specifically?

there's a patch for Intel SSDs, read this [http://sourceforge.net/projects/hdparm/forums/forum/461704/topic/3486385](http://sourceforge.net/projects/hdparm/forums/forum/461704/topic/3486385)

---

### Post by ariel on 2010-05-25
> **98cwitr said:**
> what's the error(s) specifically?

there's a patch for Intel SSDs, read this [http://sourceforge.net/projects/hdparm/forums/forum/461704/topic/3486385](http://sourceforge.net/projects/hdparm/forums/forum/461704/topic/3486385)

Thanks for the link. it appears the patch no longer works. Here's what I get:

wiper-intel2.sh: Linux SATA SSD TRIM utility, version 2.5, by Mark Lord.
Preparing for online TRIM of free space on /dev/sdb2 (ext4 mounted read-write at /).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (56393755 KB).. 
Syncing disks.. 
Beginning TRIM operations..

/dev/sdb:
trimming 30818304 sectors from 512 ranges
FAILED: Input/output error

/dev/sdb:
trimming 30965759 sectors from 512 ranges
FAILED: Input/output error

/dev/sdb:
trimming 30720000 sectors from 512 ranges
FAILED: Input/output error

/dev/sdb:
trimming 20283449 sectors from 338 ranges
FAILED: Input/output error
Removing temporary file..
Syncing disks.. 
Done.

---

### Post by 98cwitr on 2010-05-25
i get the same thing if I use the --commit option...


brett@brett-desktop:~/hdparm-9.28/wiper$ sudo bash wiper.sh --commit /dev/sda1

wiper.sh: Linux SATA SSD TRIM utility, version 2.6, by Mark Lord.
Preparing for online TRIM of free space on /dev/sda1 (ext4 mounted read-write at /).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (40160150 KB).. 
Syncing disks.. 
Beginning TRIM operations..

/dev/sda:
trimming 80320304 sectors from 1351 ranges
FAILED: Input/output error
Removing temporary file..
Syncing disks.. 
Aborted.


I think the drive cant be mounted...I'm going to try it with the live cd...brb (hopefully).


EDIT: Nope, in Live CD right now and still errors off with the drive unmounted...damnit. Emailed Mark Lord, will reply back when he does or I find something else out.

EDIT2: Upgrading kernel to 2.6.34...brb


EDIT3:....and had to reload my machine after plymouth took a crap. Now I'm getting more errors on the SSD and 10MB/s less than the initial bench.

---

### Post by 98cwitr on 2010-05-27
bump...trying to keep this going. Seems a lot of people are having this issue.

---

### Post by antiram on 2010-06-10
@98cwitr
it seems you have a sandforce ssd, then use this patched wiper
[http://www.ocztechnologyforum.com/forum/showthread.php?60882-wiper.sh-discussion-thread-(Linux-TRIM-tool)&p=516945&viewfull=1#post516945](http://www.ocztechnologyforum.com/forum/showthread.php?60882-wiper.sh-discussion-thread-(Linux-TRIM-tool)&p=516945&viewfull=1#post516945)

eg. 
./wiper-hw.sh --commit --sandforce /dev/sda1

---

### Post by ShakeyJake on 2010-06-12
Right guys, OP here. 

Thanks to this thread I did indeed get TRIM working, it just looks like the controller on my SSD has given up the ghost. OCZ have it back now and I'm getting a new one shortly.

---

### Post by Jordanwb on 2010-06-13
Where can I download the wiper script? I've been trying to use meerkat's hdparm to send a TRIM command but apparently "hdpark --trim-sector-range 0:6000000 /dev/sdc" isn't a valid sector range.

I'm beginning to feel like my avatar.

---

### Post by 98cwitr on 2010-09-15
> **Jordanwb said:**
> Where can I download the wiper script? I've been trying to use meerkat's hdparm to send a TRIM command but apparently "hdpark --trim-sector-range 0:6000000 /dev/sdc" isn't a valid sector range.

I'm beginning to feel like my avatar.

better late than never 

[http://sourceforge.net/projects/hdparm/files/](http://sourceforge.net/projects/hdparm/files/)

---

