---
title: "Linux Question to Ubuntu Users"
date: 2010-06-13
forum: General Help
---

### Post by ozzman2 on 2010-06-13
How can I assign a directory to a specific partition (another hard drive)?

I found something close here;
[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

How would someone move */home/username/music* to another drive or partition? But do so in a way that it no longer writes MP3's (or FLAC) files in the original directory of the root drive?

:guitar:

---

### Post by robvas on 2010-06-13
You can mount your music folder to that location, and have that folder reside on another drive.

---

### Post by ozzman2 on 2010-06-13
Are there multiple ways of doing something like that?

Should I be going into [I]/etc/fstab ?
[/I]

---

### Post by bodhi.zazen on 2010-06-13
Assuming you have a partition /dev/sda2 , and a mount point of /home/your_user/music

you add an entry to fstab

/dev/sda2 /home/your_user/mp3 auto defaults 0 2

See:

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by ozzman2 on 2010-06-14
That's a pretty crazy thread on how to fstab.  I'm still trying to wrap my head around all this Linux stuff.  Maybe someone can help me understand this a little better.

The operating system is located on hard drive */dev/sda1* (it also has /dev/sda5 as a logical partition for swap space, and */dev/sda6* "unallocated" for another OS in the future).

I add a second physical hard drive which becomes */dev/sdb*.

What you're saying is that I would edit the fstab entry to include:* /dev/sdb1 /home/username/Music auto defaults 0 2*

Would I then manually create a directory in the root of sdb1 called */home/username/Music*?  Or would Ubuntu somehow manage this automatically?

---

### Post by Ryan Dwyer on 2010-06-14
No, you don't need to create a directory in sdb1. Otherwise you would have /home/username/Music/Music. Your files should go in the root of the disk.

I would first move your music to a separate folder (eg. /home/username/Documents/Music-temp/). Check that /home/username/Music is indeed empty, then use the mount command to mount sdb1 to /home/username/Music. Copy your music files back. Then add your line to fstab, reboot and check that it's mounted automatically.

---

### Post by v1ad on 2010-06-14
mkdir 1
mount sda3 ./1

something similar to that. 

do man mount

---

### Post by ozzman2 on 2010-06-14
So the fstab thing will work, but any files I assign to the */home/username/Music* directory will ultimately end up in the root of sdb.

What if I wanted to do the same thing with a second or third directory?  For example: */home/username/Movies* and */home/username/Documents*.

All my music, movie and document files would then end up in the root of sdb.  I'm trying to set this up so that I have some subdirectories on sdb1 (in case I ever want to access this drive in the future from another distro).

Am I simply going about doing this in the wrong fashion?



Sorry v1ad, I don't know what you're trying to tell me.

---

### Post by Ryan Dwyer on 2010-06-14
You might want to consider storing your entire /home on sdb1. That way you can blow away your main OS, install something else and still have all your files and programs configured the way you like them.

If you want to do it the way you said, one way would be to make multiple partitions on sdb and mount one to each folder (Music, Movies, Documents etc). Another way would be to have one partition on sdb, mount it somewhere, then symlink each folder to the appropriate directories.

---

### Post by ozzman2 on 2010-06-14
So am I getting this right?

_Under the fstab method:_
I  would have multiple partitions representing each directory if I wanted  any sort of directory structure to be maintained on sdb1.

Question:   If I simply dumped all these files into the root of ***[COLOR=Blue]sdb1[/COLOR]***, how does Ubuntu manage them so that  they appear in the subdirectories on **[COLOR=Red]sda1[/COLOR]**  (ie. music, movies, docs)?


_Under the symlink mechod:_
Directories  appear almost as a hyperlink does on a web page.
it would behave  similar to this;

> [COLOR=Red]**sda1**[/COLOR][I]
/home/username/music  (symlink to **[COLOR=Blue]sdb1[/COLOR]** /music[/I])
*/home/username*/movies * (symlink to [COLOR=Blue]**sdb1**[/COLOR] /movies*)
*/home/username*/docs * (symlink to **[COLOR=Blue]sdb1[/COLOR]** /docs*)Do  I have this right so far?



What I'm trying to do is set  up a media PC.  I want the operating system on it's own partition.  I am  not interested in moving the entire */home* directory to another  partition (I would like to keep programs with the OS).

As long as  I have the media files on [COLOR=Blue]**sdb1**[/COLOR], I'm  sure I'll open them with some program in the future.  I'm not concerned  with preserving every aspect of the /home directory (with all it's  programs and settings).  I just want the subdirectories for music,  movies and games on a separate hard drive.  *Unless of course there is  no reason to put the files in sub directories on sdb1.*

If  you can seamlessly integrate the /home directory on another drive, what  is the best way to do the same thing for specific directories found  within /home?

---

### Post by bodhi.zazen on 2010-06-14
> **ozzman2 said:**
> So am I getting this right?

_Under the fstab method:_
I  would have multiple partitions representing each directory if I wanted  any sort of directory structure to be maintained on sdb1.

Question:   If I simply dumped all these files into the root of ***[COLOR=Blue]sdb1[/COLOR]***, how does Ubuntu manage them so that  they appear in the subdirectories on **[COLOR=Red]sda1[/COLOR]**  (ie. music, movies, docs)?


_Under the symlink mechod:_
Directories  appear almost as a hyperlink does on a web page.
it would behave  similar to this;

Do  I have this right so far?



What I'm trying to do is set  up a media PC.  I want the operating system on it's own partition.  I am  not interested in moving the entire */home* directory to another  partition (I would like to keep programs with the OS).

As long as  I have the media files on [COLOR=Blue]**sdb1**[/COLOR], I'm  sure I'll open them with some program in the future.  I'm not concerned  with preserving every aspect of the /home directory (with all it's  programs and settings).  I just want the subdirectories for music,  movies and games on a separate hard drive.  *Unless of course there is  no reason to put the files in sub directories on sdb1.*

If  you can seamlessly integrate the /home directory on another drive, what  is the best way to do the same thing for specific directories found  within /home?


You are getting it ...

In order to use links, you would need to mount /dev/sdb1 somewhere.

Imagine we mount it at /media/sdb1

```
sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
```Set ownership and permissions:

```
sudo chown you:you /media/sdb1
sudo chmod 770 /media/sdb1
```Now make directories

```
mkdir ~/{music,movies,doc}
mkdir /media/sdb1/{music,movies,docs}
```Now make links

```
ln -s /media/sdb1/music ~/music
ln -s /media/sdb1/movies ~/movies
ln -s /media/sdb1/docs ~/docs
```To make all this automatic, add some lines to fstab (if you add these lines to fstab, you do NOT need all those links above).

> /dev/sdb1 /media/sdb1 auto defaults 0 2
/media/sdb1/music  /home/you/music none bind 0 0
/media/sdb1/movies  /home/you/movies none bind 0 0
/media/sdb1/docs  /home/you/docs none bind 0 0

---

### Post by ozzman2 on 2010-06-15
Is there a chance the directories on sdb1 would become hard-linked somehow to the specific OS installed on sda1?  Or would that drive remain universally accessible to other Linux operating systems?  For example, if I mounted the hard drive sdb1 into "Ubuntu 15.04" one day (in the future), would sdb1 simply mount as a media drive, with access to all directories and files contained within it?  Or could I end up with some sort of error message?

Are there any advantages/disadvantages between the symlink and fstab methods?  If I added another hard drive (sdc1) with the same directories on it (music, movies, etc), would it be a similar procedure to integrate it with the OS?

Thank you guys for being patient while I ask a million questions.  I'm trying to come up with a long term solution for storing files.  I'm tired of trying to "find the files I want to keep" and copying them from an old OS to a new OS.  When I get a new OS, I want a clean install.  Linux programs are free (and always getting better).  Why do I need to carry anything more than my files forward into the future?

I hope I'm going about doing this the right way.  I have an idea what I want to do, but I'm one of those guys who knows just enough about Linux to be dangerous.  I realize trial and error is the best way to learn, but I don't want to end up screwing myself 4 years down the road from now with "I should have done this instead".  I really appreciate all the help so far.  :p

---

### Post by The Cog on 2010-06-15
> **ozzman2 said:**
> Is there a chance the directories on sdb1 would become hard-linked somehow to the specific OS installed on sda1?  Or would that drive remain universally accessible to other Linux operating systems?  For example, if I mounted the hard drive sdb1 into "Ubuntu 15.04" one day (in the future), would sdb1 simply mount as a media drive, with access to all directories and files contained within it?  Or could I end up with some sort of error message?
No chance. Hard links don't happen by accident, and cannot happen at all between partitions (for hard links, all the references must be on the same partition).
> Are there any advantages/disadvantages between the symlink and fstab methods?  If I added another hard drive (sdc1) with the same directories on it (music, movies, etc), would it be a similar procedure to integrate it with the OS?
They are different things. The fstab entry gets the partition mounted somewhere into the filesystem, wherever you choose. If you only want the partiton to contain one folder, then you might as well mount it directly into that folder. But if (as in your case) you want it to contain several different folders and put them into different places in your tree, then it makes sense to mount it somewhere else like /mnt/sdb. Then you can symlink into folders within sdb from wherever you want. The point is, you can only mount a whole partition, you can't mount a subtree of a partition.
> 

Thank you guys for being patient while I ask a million questions.  I'm trying to come up with a long term solution for storing files.  I'm tired of trying to "find the files I want to keep" and copying them from an old OS to a new OS.  When I get a new OS, I want a clean install.  Linux programs are free (and always getting better).  Why do I need to carry anything more than my files forward into the future?I like to carry some personal settings forwards. They are pretty-much all hidden in hidden files/folders in my home directory. Frinstance, my firefox bookmarks, passwords etc are in .mozilla. However, when I changed from Karmic to Lucid, so may settings weren't quite right (especially gnome desktop settings) I ended up clearing out my home completely and then just copying back a few settings like .mozilla on an as-needed basis. I suppose that gets rid of all the accumulated cruft.
> 
I hope I'm going about doing this the right way.  I have an idea what I want to do, but I'm one of those guys who knows just enough about Linux to be dangerous.  I realize trial and error is the best way to learn, but I don't want to end up screwing myself 4 years down the road from now with "I should have done this instead".  I really appreciate all the help so far.  :pIf I could only recommend one thing, it would be to keep your backups up to date. That's the one thing you are likely to regret most, if you don't do it.

---

### Post by ozzman2 on 2010-06-15
I have discovered a new variable in this.  :???:

I was going to try set up a few symlinks tonight.  As it turns out, my "sdb" is actually "sdf".

The new question is:
How does Linux assign the suffix to "sd*...*"?

If I were to add a peripheral to the system, what would keep the current "sdf" from becoming "sdg" or going back and becoming "sde"?  Wouldn't a change like that break my symlinks?

---

### Post by bodhi.zazen on 2010-06-17
> **ozzman2 said:**
> I have discovered a new variable in this.  :???:

I was going to try set up a few symlinks tonight.  As it turns out, my "sdb" is actually "sdf".

The new question is:
How does Linux assign the suffix to "sd*...*"?

If I were to add a peripheral to the system, what would keep the current "sdf" from becoming "sdg" or going back and becoming "sde"?  Wouldn't a change like that break my symlinks?

In the event of multiple devices , the designation /dev/sdxy can be unpredictable.

If you have multiple devices, mount by either label or uuid, see the fstab link I gave you earlier.

---

### Post by ozzman2 on 2010-07-04
I went through your fstab tutorial.

Didn't want the drive to show in "places" or on my desktop, so I opted to mount it under /mnt.  (Created the mount point with *sudo mkdir /mnt/music001*)

I then added these lines to my fstab (music001 is also the label on the hard drive):
[I]LABEL=music001 /mnt/music001 auto defaults 0 2
/mnt/music001 /home/anon/Music none bind 0 0
[/I]
then I changed the permissions in terminal:
[I]sudo chown username:users /mnt/music001
sudo chmod 770 /mnt/music001[/I]

seems to be working good now.
thanks

---

