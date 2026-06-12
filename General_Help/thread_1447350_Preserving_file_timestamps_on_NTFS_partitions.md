---
title: "Preserving file timestamps on NTFS partitions"
date: 2010-04-05
forum: General Help
---

### Post by rastan on 2010-04-05
[FONT=Verdana]This is driving me nuts. I'm using two NTFS formatted partitions. One is internal and holds all my data. The other is on an external hard disk and is where I back up all my data to. What I'd like to do is copy all my files from the data partition to the backup partition and preserve all the windows' timestamps (including the file creation dates).

How hard can this be? Well it appears that in the case of Ubuntu the answer is very hard indeed.
[/FONT][FONT=Verdana]
I'm aware that Linux does not support the concept of a file creation date natively. However, according to the ntfs-3g website, all of the windows' timestamps (including the creation date) are mapped on to the system.ntfs_times extended attribute ([link]("http://www.tuxera.com/community/ntfs-3g-advanced/extended-attributes/")). So if you preserve the extended attributes when making a copy then, in theory at least, the timestamps should also be preserved.

I read on another forum that a file's timestamps will be listed (albeit in an unreadable hex format) if you run the following command:

getfattr -h -e hex -n system.ntfs_times <filename>

Unfortunately however, I just cannot get it to work. With every file I've tried I simply get a message saying "no such attribute".

I would be grateful if anyone could help me.

Thanks in advance.[/FONT]

---

### Post by kblft on 2010-04-05
As far as I remember - when you copy / move files between devices - even in windows they get new creation dates. Not sure though... 

You can try to create a tarball of your files ( man tar / right click + compress - and choose .tar).
Tarballs preserve timestamps - not sure if it wil work with ntfs - but it's worth a try...

---

### Post by john newbuntu on 2010-04-05
You could also try the "cp" command with -p option
or
the "rsync" command with the "-X" option.

For the complete command options, please refer to the man pages or google it.

---

### Post by rastan on 2010-04-05
> **kblft said:**
> As far as I remember - when you copy / move files between devices - even in windows they get new creation dates. Not sure though... 

Indeed. Windows also has a very cavalier approach to timestamps.

The reason why I need to preserve all timestamps is because I've got some photos on my hard disk and I use the timestamps to know when they were taken.

Before I knew any better, I used to copy photos to my hard disk using either Microsoft's crappy camera wizard, or the standard Windows drag and drop copy. The trouble is that the two copy methods are inconsistent. One of them preserves only the creation date and the other preserves only the modified date! So I've got some files with a correct creation date, and some with a correct modification date.

Ideally, I'd like some sort of utility that could go through all my files and set the modified date to either the creation date, or the modified date, whichever of the two is the earliest. I could then ignore the creation date altogether. However, until I've worked out a way to do that I'll have to live with preserving both dates.

---

### Post by john newbuntu on 2010-04-06
Now, as far as the photos go, were they taken from a digital camera and then copied to the hard drive? If so, you could just point the cursor on the thumbnail/icon and it tells you when the picture was taken.  This is because of the metadata that gets stored with the picture.  Does this meet your requriements?
There might be some tools out there to capture this date(such as febooti or setfiledate on windows).

---

### Post by rastan on 2010-04-18
> **john newbuntu said:**
> Now, as far as the photos go, were they taken from a digital camera and then copied to the hard drive? If so, you could just point the cursor on the thumbnail/icon and it tells you when the picture was taken.  This is because of the metadata that gets stored with the picture.  Does this meet your requriements?
There might be some tools out there to capture this date(such as febooti or setfiledate on windows).

Yes I have considered that. It's definitely at least a partial solution.

I actually came across a Linux utility a while back (unfortunately I can't remember its name) that converts a file's modified date to match the EXIF modified date. However, I'm not sure that all my photos have accurate EXIF dates embedded in them so I'd also like the additional security of being able to preserve the original NTFS timestamps as well.

---

### Post by ubfu on 2010-04-18
Hi guys , this topic is similar with what I wanted to preserve the time stamps.Rather than preserve , i wanted to backup and reedit again.

[http://ubuntuforums.org/showthread.php?t=1448307](http://ubuntuforums.org/showthread.php?t=1448307)

I also hope someone would help me out to write a script for backup.
Thank you

---

### Post by coffeecat on 2010-04-18
@rastan, how are you mounting the partitions? Both with /etc/fstab? If so, please post your /etc/fstab.

If you use the manual option at the partitioning stage of the live CD installer and get the installer to create an /etc/fstab entry, it does so with options that cause timestamps to be reset. The installer's line is of the form:

```
device     mountpoint     ntfs    defaults,nls=utf8,umask=007,gid=46    0  0
```It's the umask=007 and gid=46 that cause the problem - and they're completely superfluous anyway. But if you use a simple:

```
device     mountpoint     ntfs     defaults     0  0
```... the problem goes away.

More discussion on this thread:

[http://ubuntuforums.org/showthread.php?t=1330407](http://ubuntuforums.org/showthread.php?t=1330407)

This has been going on since Hardy. Yes, I have filed a bug report. Yes, it was ignored. :roll:

---

### Post by rastan on 2010-04-18
[FONT=Verdana]Anyway, I've now found a partial solution. The problem was that Ubuntu comes installed with a very out of date version of the ntfs-3g driver. Disappointingly, even the version in the repository is out of date. So I went to the ntfs-3g site and installed their latest driver the old fashioned way (i.e. by running make on the command line).

The getfattr command I mentioned earlier in the thread will now output the system.ntfs_times attribute as expected. Setfattr also works.

However, there are still some annoying issues. All the standard Linux/Unix utilities such as cp and rsync appear to preserve the user extended attributes. However, they don't appear to be able to recognise the system entended attributes.

getfattr and setfattr also appear to exhibit similar behaviour. You can read and write to a specific system attribute. But it's not possible to list the system attributes that are available.

I'm not sure whether this restriction is standard and deliberate Linux behaviour, or whether it's just the way that the ntfs-3g driver has been written. But whatever the reason, it's extremely annoying, and it renders all the standard Linux utilities completely useless for my purposes.

What I've managed to do to get round the problem is to use getfattr to dump all the system.ntfs_times parameters into a text file. Fortunately getfattr allows this to be done recursively over a range of files. Once the copying has been done, I'm then able to use setfattr to restore the parameters from the text file to the copied files. It works surprisingly well but it's clumsy. It's fine for archiving but I really don't want to have to go through that hassle every time I copy a single file from A to B.[/FONT]
 

 [FONT=Verdana]I have to say that this whole issue has left me feeling slightly disillusioned with Linux in general and Ubuntu in particular.[/FONT]
 

 [FONT=Verdana]The ability to copy files (and all their attributes) reliably and consistently is not something that's unusual and esoteric, it's a fundamental requirement for any modern operating system. Issues such as this will need to be addressed if Linux is ever to gain mainstream acceptance.

[/FONT]

---

### Post by rastan on 2010-04-18
> **ubfu said:**
> Hi guys , this topic is similar with what I wanted to preserve the time stamps.Rather than preserve , i wanted to backup and reedit again.

[http://ubuntuforums.org/showthread.php?t=1448307](http://ubuntuforums.org/showthread.php?t=1448307)

I also hope someone would help me out to write a script for backup.
Thank you

If you're able to read your original drive from Ubuntu, then what you're trying to achieve could be done using setfattr and getfattr. See the following link for further details.

[http://tg-linux.blogspot.com/2005/06/extended-file-system-attributes.html](http://tg-linux.blogspot.com/2005/06/extended-file-system-attributes.html)

---

### Post by rastan on 2010-04-18
> **coffeecat said:**
> @rastan, how are you mounting the partitions? Both with /etc/fstab? If so, please post your /etc/fstab.


Hmmm, I wasn't aware that there was also a problem with the way that Ubuntu mounts drives. Not good. Not good at all.

The drive I've been using for testing is housed in an external USB enclosure and it automatically mounts when I plug it in. I'm not actually sure how to configure the behaviour of external automounting USB drives. Can you point me in the right direction?

Anyway, I've also got a permanently mounted NTFS partition. And my /etc/fstab file looks like this:

```
proc /proc proc defaults 0 0
UUID=90fab3f8-5140-4ba4-9278-f89359876d8c / ext4 errors=remount-ro 0 1
UUID=ee7c6f95-f304-476d-8468-eaf79541ccad none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda2 /media/New\040Volume ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sda1 /media/windows_xp ntfs-3g defaults,locale=en_GB.UTF-8 0 0
```

---

### Post by coffeecat on 2010-04-18
Well - I'm puzzled. Your fstab line for sda1 should be fine - at least for the timestamp problem I've come across. And I've never had a problem with timestamps with automagically mounted external NTFS partitions.

The issue I found with the fstab line that contains "defaults,nls=utf8,umask=007,gid=46" was particularly when I copied from an ext3/4 partition to the NTFS partition. Tbh honest, I can't remember whether it happened on other occasions or not. Interestingly, if I did a 'cp -a' (or 'cp -p') I got a "cp: preserving times for `/path/to/file': Operation not permitted" error. 

Sorry I can't be of more help. Did you read the link I posted? The OP and I discussed quite a bit and the OP, less world-weary than me, came up with some interesting things. Whether they might be of help, I don't know.

---

### Post by fig_wright on 2010-08-09
> **coffeecat said:**
> @rastan, how are you mounting the partitions? Both with /etc/fstab? If so, please post your /etc/fstab.

```
device     mountpoint     ntfs     defaults     0  0
```... the problem goes away.

More discussion on this thread:

[http://ubuntuforums.org/showthread.php?t=1330407](http://ubuntuforums.org/showthread.php?t=1330407)

This has been going on since Hardy. Yes, I have filed a bug report. Yes, it was ignored. :roll:

Sweet. That solved this annoying problem for me :p

---

### Post by tk83 on 2011-01-11
I came across this thread and can't help commenting: the file creation date is just that - it's the date that the file was physically created in the file system. This means that if you copy or move the file to a different file system (for example a USB disk for your backups) then the creation date is liable to change.

This is true for both Linux and Windows and trying to pretend that this date is something else and shoehorn it into being that will just lead to confusion and problems.

It is of course **very important to keep the date that a particular photo was taken**, not to mention other important attributes of the photo such as camera settings, comments/description and location (if available from the camera). This is all kept in the EXIF metadata which is part of the JPEG file and is thus immune to being lost or altered by file system copy and move operations. 

Use any decent photo manager (digikam or Google Picasa come to mind on Linux, there are dozens on Windows) and this will show your photos in the proper date order by reading the EXIF metadata.

---

### Post by Mark Phelps on 2011-01-11
To get back to the original question ...

The ability to preserve file date-time stamps when copying files in MS Windows is critically dependent on the file manager app used to do the copying.

Back in the old days (e.g., Norton file manager), preserving the dates was commonplace, but more recent tools have removed that feature -- except one: DirectoryOpus.

I use that file manager all the time and its DEFAULT is to preserve the file date-time stamps.  This proves very handy when copying files to another system for backup purposes -- and then going back later to see the original dates of the files.

---

### Post by coffeecat on 2011-01-11
> **tk83 said:**
> I came across this thread and can't help commenting: the file creation date is just that - it's the date that the file was physically created in the file system. This means that if you copy or move the file to a different file system (for example a USB disk for your backups) then the creation date is liable to change.

This is true for both Linux and Windows and trying to pretend that this date is something else and shoehorn it into being that will just lead to confusion and problems.

That is a very strange comment. The long and the short and tall of it is that changing the date/timestamp when a file is copied is **data corruption**. When I copy a file from one filesystem to another in Linux I expect the timestamp to be preserved. It usually is. When a file manager fails to do this it is considered a bug - because it is a bug.

When I copy a file from one filesystem to another in MacOS, I expect the timestamp to be preserved. It is.

When I copy a file from one filesystem to another in Windows...

> **Mark Phelps said:**
> The ability to preserve file date-time stamps when copying files in MS Windows is critically dependent on the file manager app used to do the copying.

Back in the old days (e.g., Norton file manager), preserving the dates was commonplace, but more recent tools have removed that feature -- except one: DirectoryOpus.

Thanks for the warning. I was needing to copy/backup a whole load of folders and contents on a NTFS partition to a NTFS USB drive. I happened to try this in Windows 7 because that was what I was booted into. I used Explorer not expecting any issue but noticed that it was changing the timestamp of all the folders (but not the files for some reason) to current. I aborted the process, deleted what had been copied and then rebooted into Ubuntu where I was able to carry out my backup using Nautilus without data corruption. And more quickly too! :rolleyes:

---

