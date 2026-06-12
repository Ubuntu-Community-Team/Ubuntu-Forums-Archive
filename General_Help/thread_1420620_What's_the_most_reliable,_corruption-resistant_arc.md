---
title: "What's the most reliable, corruption-resistant archive format?"
date: 2010-03-03
forum: General Help
---

### Post by UnrealMiniMe on 2010-03-03
I'm wanting to create a one-time snapshot archive of all my data in case something catastrophic ever happens to my main hard drive and my backup drive.  I should add that I update my main backup regularly, which means that I wouldn't notice any creeping data corruption problems until it's too late...which is another reason a one-time snapshot is so important.

Since I'm archiving a snapshot of all of my data at once, only a hard drive is big enough to handle the job.  (I'll copy a small fraction - the truly 100% irreplaceable stuff - to DVD-R's too, but that doesn't mean I particularly want to lose any of the other stuff either.)  Unfortunately, this means my storage medium doesn't inherently have any CRC's, error correction/redundancy bits, etc. built into it like data DVD's might.

**So:  What archive format would you suggest using for maximum reliability and resistance to corruption?**

My main concern is making sure that I can still open the archive and extract surviving files even if some of the bits (or the entirety of other files) go corrupt.  This is my last-ditch fallback archive, so if I ever need to use it, I really, really don't want to get a message saying the archive is corrupt and cannot be opened at all! :eek:  Because of that, it's important that the individual files and folders are compressed separately from each other...if at all.  I don't care about the compression ratio, and I'd even be happy if the archive was 150% the size of my data thanks to a gigantic recovery record. ;)  I also care about CRC's and such, since I'll want to know which files/folders/etc. are corrupt vs. which ones are still intact.

Can anyone knowledgeable about the comparative reliability of archive formats help me out here?  Thanks!

---

### Post by gsmanners on 2010-03-03
I would suggest you make some nice big tar.gz files out of stuff that isn't already big and then use par2.

To create recovery blocks you simply put:

par2 c -r5 archive.tar.gz

That will give 5% redundancy. If you then find that the file is corrupt (less than 5% is bad), then you can recover like so:

par2 r archive.tar.gz.par2 archive.tar.gz.*

---

### Post by handy on 2010-03-03
I don't know how much data you are talking about?

Is it a partition, or multiple partitions?

If it is a partition or a number of them, I would use Clonezilla & either dump a clone onto another drive, or dump image(s) of partitions onto another drive, that after the backup has been done, gets disconnected & kept somewhere else, thus protected from power spikes, fire & theft.

---

### Post by UnrealMiniMe on 2010-03-03
> **gsmanners said:**
> I would suggest you make some nice big tar.gz files out of stuff that isn't already big and then use par2.

To create recovery blocks you simply put:

par2 c -r5 archive.tar.gz

That will give 5% redundancy. If you then find that the file is corrupt (less than 5% is bad), then you can recover like so:

par2 r archive.tar.gz.par2 archive.tar.gz.*

Thank you!  I'd never heard of par2, but it sounds exactly like the kind of thing I'm looking for! :)  I'm well set on the checksum front too, since I just stumbled across the hashdeep program.  That will let me create a file containing individual hashes of all my files, and it also has an audit mode for comparing the files to the saved hashes later.

I'm still looking for a different archive format other than tar.gz though, since gzip compresses archives as a whole.  Even with the redundancy and recovery capabilities of par2, I'd still feel more comfortable with piecemeal compression of the individual files...just in case.

> **handy said:**
> I don't know how much data you are talking about?
I run the Wayback Machine, so we're looking at about 3 petabytes. ;)

Seriously though, it's just a few hundred gigs.  The spare hard drive I'm using for the occasion is easily large enough to hold it, but it's not large enough to hold two full copies unless a truly magical lossless compression algorithm is discovered sometime within the next couple days.  Technically speaking, burning a 100 spindle of DVD-R's isn't entirely insane, but that's a mess I'd like to put off a little (a lot) longer for when I really have the time. :p

> **handy said:**
> Is it a partition, or multiple partitions?

If it is a partition or a number of them, I would use Clonezilla & either dump a clone onto another drive, or dump image(s) of partitions onto another drive, that after the backup has been done, gets disconnected & kept somewhere else, thus protected from power spikes, fire & theft.

Yep, that's what I was thinking, too:  I'll be putting it somewhere cool, dry, and fireproof.  (...and protected by bottlecap mines, deathclaws, and an arsenal of high-powered weaponry, just for fun.)

---

### Post by handy on 2010-03-03
I have a machine with drive drawers, the plastic ones (which I use) cost peanuts.

It allows me to use my No.2. box for many different jobs.

One of these jobs is as a FreeNAS server.  I stick two drawers in box No.2., one has a 2GB drive carrying the FreeNAS system, the other is a 1.5TB drive that carries the backup data.

I manually add the new files from my No.1. box to the FreeNAS, when it is finished I shut down box No.2. & pull the drives.

I also have seriously important data backed up onto DVD (more than once).

FreeNAS is really easy to install & work with.  It may or may not be appropriate for your situation?

---

### Post by psusi on 2010-03-03
I was going to suggest par2 as well.  You might go with a 10% redundancy factor just to be safe.  If you are really THAT paranoid then you can just do an uncompressed tar backup and it will pick back up after any damage and manage to restore the rest of the files, but that level of paranoia is about as far out there as the guys that say the moon landing was faked.

Realistically if there is any minor damage to the backup disk par2 will fix it, so the only thing you have to worry about is the backup disk becoming so damaged it is entirely unreadable.  This too can be solved by using par2 to split the data across a dozen backup disks with 10% redundancy and even if you loose a whole disk, it will be able to recover.

---

### Post by handy on 2010-03-03
Boy I'm glad that the loss of the data on my HDD would only be a pain, & cost me a great deal of time to recover from, (to the point where I may not bother) as opposed to it being a situation where the data is essential & if lost it is unrecoverable. 

Costing me money whilst ever the data was unavailable would certainly be a huge pain, this would be the most common pain without a doubt.

Stress lives there.

Who would want to be the poor sys-admin' having to either try to recover the situation, or trying to explain why there exists no surviving backup, backup?

---

### Post by jeff.sadowski on 2010-03-04
Just thinking up ideas to try out. I don't know if it would be useful but:
You could create a raid using lvm and loopback files.
Create a bunch of files like so.

dd if=/dev/zero of=raid1disk1of6.iso bs=1024 count=716800
dd if=/dev/zero of=raid1disk2of6.iso bs=1024 count=716800
dd if=/dev/zero of=raid1disk3of6.iso bs=1024 count=716800
dd if=/dev/zero of=raid1disk4of6.iso bs=1024 count=716800
dd if=/dev/zero of=raid1disk5of6.iso bs=1024 count=716800
dd if=/dev/zero of=raid1disk6of6.iso bs=1024 count=716800

losetup /dev/loop0 raid1disk1of6.iso
losetup /dev/loop1 raid1disk2of6.iso
losetup /dev/loop2 raid1disk3of6.iso
losetup /dev/loop3 raid1disk4of6.iso
losetup /dev/loop4 raid1disk5of6.iso
losetup /dev/loop5 raid1disk6of6.iso

pvcreate /dev/loop[0-5]

vgcreate backup /dev/loop[0-5]

I forget how to raid it from here but its an idea I'll learn it further tomorrow if you think its helpful

lvcreate backup something 

then you format it and add stuff to it you could even raid 5 maybe.

---

### Post by UnrealMiniMe on 2010-03-04
> **handy said:**
> I have a machine with drive drawers, the plastic ones (which I use) cost peanuts.

It allows me to use my No.2. box for many different jobs.

One of these jobs is as a FreeNAS server.  I stick two drawers in box No.2., one has a 2GB drive carrying the FreeNAS system, the other is a 1.5TB drive that carries the backup data.

I manually add the new files from my No.1. box to the FreeNAS, when it is finished I shut down box No.2. & pull the drives.

I also have seriously important data backed up onto DVD (more than once).

FreeNAS is really easy to install & work with.  It may or may not be appropriate for your situation?

I'll be locking this particular archive in the dungeon without further modification for a long while, but a clean and modular solution like drive drawers actually sounds extremely attractive to me for my regular backups.  I generally keep my regular backup drive connected at all times, and then I rsync on occasion, but an electrical problem could wipe out both my main drive and primary backup in one strike.  I once had a nerd fantasy about storing my data on some kind of small rack server system, but I never even considered the thought that drive drawers already existed for desktops.  Maybe I live under a rock or something...

I suppose you have two drawers on your second box?  (Or do you have a larger unit taking up multiple 5.25" drive bays and capable of holding multiple drives?)  Would you suggest any particular brand or vendor, or would high-rated drawers from Newegg be as good as any others?

> **psusi said:**
> I was going to suggest par2 as well.  You might go with a 10% redundancy factor just to be safe.  If you are really THAT paranoid then you can just do an uncompressed tar backup and it will pick back up after any damage and manage to restore the rest of the files, but that level of paranoia is about as far out there as the guys that say the moon landing was faked.
Hahaha....instead of going all out with my paranoia, I'm actually kind of looking for the sweet spot where my paranoia, stinginess, and laziness curves all intersect. :)  I'm considering the [dar format]("http://en.wikipedia.org/wiki/DAR_%28Disk_Archiver%29"), which was developed to be a more modern replacement for tar.  It uses per-file gzip/bzip2 compression instead of per-archive compression, so combined with hashdeep and par2 at 10% redundancy, this archive should be pretty solid.

> **psusi said:**
> Realistically if there is any minor damage to the backup disk par2 will fix it, so the only thing you have to worry about is the backup disk becoming so damaged it is entirely unreadable.  This too can be solved by using par2 to split the data across a dozen backup disks with 10% redundancy and even if you loose a whole disk, it will be able to recover.
Wow...yeah, I don't have enough data to spread out over that many drives.  If I had a dozen drives to spare, I'd just go on and make a dozen fully redundant copies instead. :D

> **jeff.sadowski said:**
> Just thinking up ideas to try out. I don't know if it would be useful but:
You could create a raid using lvm and loopback files.
Create a bunch of files like so.

dd if=/dev/zero of=raid1disk1of6.iso bs=1024 count=716800
dd if=/dev/zero of=raid1disk2of6.iso bs=1024 count=716800
dd if=/dev/zero of=raid1disk3of6.iso bs=1024 count=716800
dd if=/dev/zero of=raid1disk4of6.iso bs=1024 count=716800
dd if=/dev/zero of=raid1disk5of6.iso bs=1024 count=716800
dd if=/dev/zero of=raid1disk6of6.iso bs=1024 count=716800

losetup /dev/loop0 raid1disk1of6.iso
losetup /dev/loop1 raid1disk2of6.iso
losetup /dev/loop2 raid1disk3of6.iso
losetup /dev/loop3 raid1disk4of6.iso
losetup /dev/loop4 raid1disk5of6.iso
losetup /dev/loop5 raid1disk6of6.iso

pvcreate /dev/loop[0-5]

vgcreate backup /dev/loop[0-5]

I forget how to raid it from here but its an idea I'll learn it further tomorrow if you think its helpful

lvcreate backup something 

then you format it and add stuff to it you could even raid 5 maybe.
This does sound cool, but I think it also sounds a bit too intricate and hands-on for my tastes.  I tend to do a clean install every Ubuntu release (in addition to trying out other distros on spare partitions every once in a while), and the less unusual settings I have to worry about maintaining, the better.

Actually, it's to the point where I have a script to handle automatically symlinking a new distro up to my data partition, which also holds my shared desktop and a few particular shared config folders (Firefox, Thunderbird, Rhythmbox database, and a couple others).  It's not exactly a separate partition for my home folder, since doing that can run into troublesome conflicts across distros, but it's close.  It seems to be working out well, so I'd like to not mess with the general structure. My regular backups are simply rsyncs of my data partition. :)

---

### Post by psusi on 2010-03-04
> **jeff.sadowski said:**
> Just thinking up ideas to try out. I don't know if it would be useful but:
You could create a raid using lvm and loopback files.
Create a bunch of files like so.

dd if=/dev/zero of=raid1disk1of6.iso bs=1024 count=716800
dd if=/dev/zero of=raid1disk2of6.iso bs=1024 count=716800
dd if=/dev/zero of=raid1disk3of6.iso bs=1024 count=716800
dd if=/dev/zero of=raid1disk4of6.iso bs=1024 count=716800
dd if=/dev/zero of=raid1disk5of6.iso bs=1024 count=716800
dd if=/dev/zero of=raid1disk6of6.iso bs=1024 count=716800

losetup /dev/loop0 raid1disk1of6.iso
losetup /dev/loop1 raid1disk2of6.iso
losetup /dev/loop2 raid1disk3of6.iso
losetup /dev/loop3 raid1disk4of6.iso
losetup /dev/loop4 raid1disk5of6.iso
losetup /dev/loop5 raid1disk6of6.iso

pvcreate /dev/loop[0-5]

vgcreate backup /dev/loop[0-5]


Naming them .iso is kinda wrong since they aren't iso filesystem images.  Also with raid 1 it would accomplish the same thing with far less effort, complexity, and be much easier to reassemble to just cp your backup file 6 times.

> **jeff.sadowski said:**
> then you format it and add stuff to it you could even raid 5 maybe.

Easier to just use par2.

> **UnrealMiniMe said:**
> 
Hahaha....instead of going all out with my paranoia, I'm actually kind of looking for the sweet spot where my paranoia, stinginess, and laziness curves all intersect. :)  I'm considering the [dar format]("http://en.wikipedia.org/wiki/DAR_%28Disk_Archiver%29"), which was developed to be a more modern replacement for tar.  It uses per-file gzip/bzip2 compression instead of per-archive compression, so combined with hashdeep and par2 at 10% redundancy, this archive should be pretty solid.

I looked at dar once and decided that it did not offer anything tar didn't, and the per file compression made for larger backups.  If you par2 the dar file and par2 is unable to repair any damage, I do not thing that dar is going to be able to do a thing with the files either.  Might be interesting to test that out though.  hashdeep won't really add anything to the picture since it will just tell you that the files were indeed restored correctly, which you really already would know from the fact that par2 and tar/dar did their job.  Actually I think dar had a good checksum on each file in the archive anyhow that it used to verify correct restoration.

---

### Post by UnrealMiniMe on 2010-03-04
> **psusi said:**
> Naming them .iso is kinda wrong since they aren't iso filesystem images.  Also with raid 1 it would accomplish the same thing with far less effort, complexity, and be much easier to reassemble to just cp your backup file 6 times.



Easier to just use par2.



I looked at dar once and decided that it did not offer anything tar didn't, and the per file compression made for larger backups.  If you par2 the dar file and par2 is unable to repair any damage, I do not thing that dar is going to be able to do a thing with the files either.  Might be interesting to test that out though.  hashdeep won't really add anything to the picture since it will just tell you that the files were indeed restored correctly, which you really already would know from the fact that par2 and tar/dar did their job.  Actually I think dar had a good checksum on each file in the archive anyhow that it used to verify correct restoration.

Actually, you're right that dar's own checksum kind of makes hashdeep redundant for verifying archives, though it would still be useful for an uncompressed tar.  I suppose hashdeep is best suited for auditing unarchived directory trees.

Anyway, I still want to steer clear of solid-compressed archives like tar.gz's.  par2's redundancy definitely helps give me peace of mind, but I don't want to put all of my eggs in one basket either, so I still prefer the tradeoffs of individual file compression to those of solid compression.  par2 notwithstanding, I've just seen too many corrupted archives to take needless chances.  Besides, I'm planning on locking this drive away, so I won't find much use for the extra space that solid compression would provide. ;)

---

### Post by psusi on 2010-03-04
If you are going to just use an uncompressed tar that's one thing; I'm just saying that if you then par2 it, then anything you gain by going uncompressed or doing dar's file by file compression is lost.  In other words, the protection provided by the two mechanisms are incompatible and par2's is far better, so I'd say just go with that and you're safe.

---

### Post by Alexandre Putt on 2010-03-04
You may want to consider ARJ.

---

### Post by UnrealMiniMe on 2010-03-04
> **psusi said:**
> If you are going to just use an uncompressed tar that's one thing; I'm just saying that if you then par2 it, then anything you gain by going uncompressed or doing dar's file by file compression is lost.  In other words, the protection provided by the two mechanisms are incompatible and par2's is far better, so I'd say just go with that and you're safe.

I'm not following you.  The way I see it, they're complementary.  All par2 does is provide redundancy files, and it doesn't modify the original archive file whatsoever.  Therefore, it makes no sense to say par2 redundancy is "incompatible" with safer compression schemes.

I can see why you might think independent file compression (or no compression) isn't going to add anything, since an archive that par2 can't reconstruct completely might not even have any salvageable files left.  Still, I doubt this is the best assumption to make, since the errors might be spread in such a way that par2 can't reconstruct the entire archive, even if most individual files are still intact.  I might be misunderstanding something here, but I'd have to learn a lot more about Reed-Solomon error correction to bridge that gap.  Even if I'm wrong, an 11% corrupted archive might still have plenty of usable files (especially if the 11% corruption is concentrated), even if 10% redundancy can't restore it.  Either way though, the worst that individual file compression (or no compression) will do is take up more space; it can't make the archive more susceptible to total failure.

---

### Post by psusi on 2010-03-04
Ohh, it has been a while since I used par2.  I was thinking that it did modify the input files so you couldn't extract them without first having par2 process them, but now that you mention it, that does make sense.

---

### Post by Sporkman on 2010-04-28
I wrote a script for solid & redundant archiving/dearchiving, which uses par2:

```
#!/bin/bash

#
# Data archiving tool, with verification and data redundancy
#
# Sporkman, 4/20/10
#
# For a given source file or directory, creates an archive directory holding the
# tar'd source as well as verification info. Specifically, the contents of the
# archive directory are:
#
# 1. The tar'd source, split into chunks,
# 2. A copy of this script (as it was when the archive was created),
# 3. A sha512sum hash check file,
# 4. A series of data files (*.par2) used by par2 to verify and repair the data
#       tar file chunks.
#
# The purpose of this utility is to enable long-term storage of data on media
# which may become corrupted over time.
#

DATA_FNAME="data.tar"
HASH_FNAME="hash"

DATA_REDUNDANCY_PCT="20"
SPLIT_FILE_SIZE="100M"

infomsg ()
{
   echo ""
   echo "$1"
}

errmsg ()
{
   infomsg "$1"
   echo ""
   exit 1
}

checkres ()
{
   if [ $1 -ne 0 ]; then
      errmsg "Failed."
   fi
}

print_usage()
{
   echo ""
   echo "Usage:"
   echo ""
   echo "   To create an archive:"
   echo ""
   echo "      archive c <source path> <dest dir> <dest name>"
   echo ""
   echo "   To extract an archive:"
   echo ""
   echo "      archive x <archive path> <dest dir>"
   echo ""
   echo "   To check (\"verify\") an archive:"
   echo ""
   echo "      archive v <archive path>"
   echo ""
   echo ""
   exit 1
}

check_archive ()
{
   # Remove any trailing slashes
   ARC="${1/%\//}"

   if [ ! -e "$ARC" ]; then
      errmsg "Error: Archive doesn't exist"
   fi
   
   if [ ! -d "$ARC" ]; then
      errmsg "Error: Archive is not a directory as it should be"
   fi
   
   infomsg "Checking archive integrity..."
   
   RETVAL=0
   
   if [ ! -e "${ARC}/${DATA_FNAME}.aaaa" ]; then
      infomsg "Error: Data file is missing"
      RETVAL=1
   fi
   
   if [ ! -e "${ARC}/${HASH_FNAME}" ]; then
      infomsg "Error: Hash file is missing"
      RETVAL=1
   fi
   
   if [ ! -e "${ARC}/${DATA_FNAME}.aaaa.par2" ]; then
      infomsg "Error: par2 verification file is missing"
      RETVAL=1
   fi
   
   if [ $RETVAL -ne 0 ]; then
      return $RETVAL
   fi

   MYPWD=`pwd`

   cd ${ARC}

   sha512sum --status -c ${HASH_FNAME}
   
   if [ $? -ne 0 ]; then
      infomsg "Error: hash verification failed"
      RETVAL=2
   fi

   cd $MYPWD
   
   if [ $RETVAL -ne 0 ]; then

      par2 v -qq ${ARC}/${DATA_FNAME}.*
   
      if [ $? -ne 0 ]; then
         infomsg "Error: par2 verification failed"
      fi
   fi
   
   return $RETVAL
}

create_archive ()
{
   # Remove any trailing slashes
   SRC="${2/%\//}"
   DST="${3/%\//}"
   NM="${4/%\//}"

   SRCDIR=`dirname ${SRC}`
   SRCNM=`basename ${SRC}`

   if [ ! -e "$SRC" ]; then
      errmsg "Error: Source path doesn't exist"
   fi
   
   if [ ! -e "$DST" ]; then
      errmsg "Error: Destination directory doesn't exist"
   fi
   
   if [ ! -d "$DST" ]; then
      errmsg "Error: Destination directory is not a directory"
   fi
   
   if [ -e "${DST}/${NM}" ]; then
      errmsg "Error: Destination name already exists"
   fi
   
   infomsg "Creating archive directory..."
   
   mkdir ${DST}/${NM}
   
   checkres $?
   
   cp ${0} ${DST}/${NM}
   
   checkres $?
   
   infomsg "Archiving source data..."
   
   MYPWD=`pwd`
   
   cd "${SRCDIR}"
   checkres $?
   
   ARCDIR="${DST}/${NM}"

   if [ "${DST:0:1}" != "/" ]; then
      ARCDIR="${MYPWD}/${ARCDIR}"
   fi

   FNAME="${ARCDIR}/${DATA_FNAME}"
   
   tar --totals -cv ${SRCNM} | split --bytes=${SPLIT_FILE_SIZE} --suffix-length=4 - ${FNAME}.
   
   checkres $?
   
   cd "${ARCDIR}"
   checkres $?
   
   infomsg "Calculating hash..."
   
   for f in `ls -1 ${DATA_FNAME}.*`; do
      sha512sum -b ${f} >> ${HASH_FNAME}
   done
   
   checkres $?
   
   cd "${MYPWD}"
   checkres $?
   
   infomsg "Generating redundancy data..."
   
   for f in `ls -1 ${FNAME}.*`; do
      par2 c -qq -r${DATA_REDUNDANCY_PCT} ${f}
   done
   
   checkres $?
   
   check_archive "${ARCDIR}"
   
   checkres $?
}

extract_archive ()
{
   # Remove any trailing slashes
   ARC="${2/%\//}"
   DST="${3/%\//}"
   
   if [ ! -e "$DST" ]; then
      errmsg "Error: Destination directory doesn't exist"
   fi
   
   if [ ! -d "$DST" ]; then
      errmsg "Error: Destination directory is not a directory"
   fi
   
   check_archive "$ARC"
   
   RES=$?
   
   if [ $RES -eq 1 ]; then
   
      errmsg "Error: Archive is incomplete. Extraction will need to be done manually."
      
   elif [ $RES -eq 2 ]; then
   
      infomsg "Warning: Archive appears to be corrupted. Will attempt to repair..."
      
      MSG=0
      
      for f in `ls -1 ${ARC}/${DATA_FNAME}.*`; do
         par2 r "${f}.par2"
      
         if [ $? -ne 0 ]; then
            if [ $MSG -eq 0 ]; then
               infomsg "Archive repair was unsuccessful. Will attempt to extract anyways."
               MSG=1
            fi
         fi
      done
          
   else
      infomsg "Archive looks ok."
   fi
   
   infomsg "Extracting archive to ${DST} ..."
   
   infomsg "(Output suppressed - see ${DST}/archive_x_log for details)"
   
   MYPWD=`pwd`
   
   cd ${DST}
   checkres $?
   
   TARFILE="${ARC}/${DATA_FNAME}"

   if [ "${ARC:0:1}" != "/" ]; then
      TARFILE="${MYPWD}/${TARFILE}"
   fi

   cat ${TARFILE}.???? | tar -xv  > archive_x_log 2>&1
   
   checkres $?
   
   cd "${MYPWD}"
   checkres $?
}


#
#
#
#

if [ "`which tar`" == "" ]; then
   errmsg "Error: tar needs installed"
fi

if [ "`which par2`" == "" ]; then
   errmsg "Error: par2 needs installed"
fi

if [ "`which sha512sum`" == "" ]; then
   errmsg "Error: sha512sum needs installed"
fi

MODE="${1}"

if [ "$MODE" == "c" ]; then

   if [ $# -ne "4" ]; then
      print_usage
   fi
   
   create_archive "$@"
   
elif [ "$MODE" == "x" ]; then

   if [ $# -ne "3" ]; then
      print_usage
   fi
   
   extract_archive "$@"
   
elif [ "$MODE" == "v" ]; then

   if [ $# -ne "2" ]; then
      print_usage
   fi
   
   shift
   check_archive "$@"
   
   RES=$?
   
   if [ $RES -eq 1 ]; then
   
      errmsg "Error: Archive is incomplete. Extraction would need to be done manually."
      
   elif [ $RES -eq 2 ]; then
   
      infomsg "Warning: Archive appears to be corrupted."
            
   else
      infomsg "Archive looks ok."
   fi

else

   print_usage
   
fi

infomsg "Done."
echo ""
exit 0

```

---

