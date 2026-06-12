---
title: "Looking for media solution"
date: 2011-02-15
forum: General Help
---

### Post by stad on 2011-02-15
Attention Mods: Please feel free to move thread if not appropriately categorized.

I recently just purchased a netbook to travel with me for school and work. It currently dual-boots Windows 7 and Ubuntu Netbook edition. I also have a relatively recent (within 5 years) desktop computer (triple core AMD, x64, 4GB RAM, 500GB HD) currently running Ubuntu 10.10. I'll tell you what I need to do, and hopefully someone will have a solution for me. 

1. I need any version of Windows because I have two iPods (an old one and a new 4th gen. iTouch). I am not interested in a Linux solution for managing because frankly, it just doesn't work as well. 

2. I would like to have my iTunes Library be on a separate machine/drive (ex. Manage iPods from netbook but have all songs saved on desktop). 

3. I also use the program Java PS3 Media Server. It runs on Ubuntu and basically streams media to my Playstation which plays on my TV. 

Is this possible? I know nothing of Ubuntu Server, but perhaps this would be the best way? Please let me know if you need more information, otherwise please make suggestions. Thanks in advance!

---

### Post by blueridgedog on 2011-02-15
The simple approach them seems to be to place your media on the desktop and share the folder with other systems ([http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)).  The other systems will map a drive (if windows) or a path (if nix or mac) to the samba share on the desktop.  You would then delete and rebuild your music library, pointing to the new location.  The media streaming software would then be installed on the desktop and configured to source the location of the files.

As far as ipods and iphones, linux supports them now almost as well as windows (better in my opinion as you no longer have to deal with itunes).

Take a look:  [http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

---

### Post by stad on 2011-02-15
Thank you! That does seem to be easiest. I will research this Samba thing more when time permits. 

As far as the libimobile link, the site says that it will only work for iPod touches. My girlfriend has one, but I still have the old 30GB iPod Video. As far as I know, I still need Windows, right?

---

### Post by PaulReaver on 2011-02-15
i thought banshee and rhthymbox could manage ipod video???

i'm pretty sure banshee can

---

### Post by blueridgedog on 2011-02-15
> **stad said:**
> My girlfriend has one, but I still have the old 30GB iPod Video. As far as I know, I still need Windows, right?

I think the older version was already supported.  I have had most ipods and used them all with Linux...especially now that libmobiledevices is out.

---

### Post by stad on 2011-02-15
> **PaulReaver said:**
> i thought banshee and rhthymbox could manage ipod video???

i'm pretty sure banshee can

I have heard of too many problems with this program. I'm looking for something that would do what iTunes would do without sacrificing too much.

> **blueridgedog said:**
> I think the older version was already supported.  I have had most ipods and used them all with Linux...especially now that libmobiledevices is out.

I will definitely check this out. The only thing that comes to mind now is how to manage two ipods. Might be ignorance, but it seems the best(read "easiest") way (in Windows) to manage two ipods was to have multiple users. Is this the same for Ubuntu with libmobiledevices?

---

### Post by stad on 2011-02-22
I wanted to give you an update blueridgedog. I got my (older iPod) working under Banshee and you are right, much better than iTunes. On the fly syncing and you don't even have to have the songs saved in your library!

Now the bad news... Regardless of what anyone says, I'm convinced that the 4th Gen iPod Touch with OS 4.1 does not work in Ubuntu. I have it jailbroken, it shows up in banshee, I can see the song saved to it, but it will not sync any songs from Banshee.

---

