---
title: "Syncing music folder and banshee"
date: 2011-11-20
forum: General Help
---

### Post by qleak on 2011-11-20
We have multiple laptops in our house and a NAS that allows NFS, FTP, CIFS connections. I'm working on setting up an autofs, curlftpfs & unison synchronization for our music folders. Hopefully to fully automate since my wife buys songs and then doesn't back them up. 

I think I will be okay setting up the filesystems to automatically mount when in our local network and to synchronize between the music folders with unison. 

Does anyone know a way to make banshee rescan it's music folder or import particular files without going through the graphical interface?

In particular i'm concerned that a new file will be transfered

Laptop1 -> NAS -> Laptop2

but then banshee on laptop2 will not recognize the file unless it's scanned.

Anyone set up anything like this? Any suggestions?

---

### Post by hwttdz on 2011-11-20
I don't use banshee, but most media players have a "watch my library for new files" option.  So, just set your media library folder correctly (~/Music) and tell it to watch.

[http://ubuntuforums.org/showthread.php?t=1785883](http://ubuntuforums.org/showthread.php?t=1785883)

---

### Post by qleak on 2011-11-20
> **hwttdz said:**
> I don't use banshee, but most media players have a "watch my library for new files" option.  So, just set your media library folder correctly (~/Music) and tell it to watch.

[http://ubuntuforums.org/showthread.php?t=1785883](http://ubuntuforums.org/showthread.php?t=1785883)

I forgot to mention, banshee's option to watch files for updates causes doubled entries in the database every time a cd is imported or song is downloaded from amazon. so I'm looking for a command line, if possible.

---

### Post by hwttdz on 2011-11-20
So just to be clear:
When you rip a cd or download a file from amazon, the file goes where (I assume the ~/Music on the local machine)? 

And then from there it goes to /media/Music on the NAS?

And from there it goes to ~/Music on all the machines?  

And the issue is that banshee will either 
a) not notice new music in the ~/Music dir if the watch my folder is unchecked, or 
b) it will create two entries for a single file in its database?  if the watch my library box is checked.

Is that all right, I also assume ~/Music is not where they live on the local machines (because then you'd be keeping multitudinous copies), so maybe we'll call that /localmachine/Music.

Do you have the "copy files to media folders when importing" enabled?

Does the machine from which the media was purchased/ripped handle this properly?  

Oh, and welcome to the forum, seems like you're not new to linux on the whole (that's a pretty complicated syncing scheme you're describing).

---

