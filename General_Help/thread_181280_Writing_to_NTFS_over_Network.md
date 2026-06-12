---
title: "Writing to NTFS over Network?"
date: 2006-05-23
forum: General Help
---

### Post by unnes on 2006-05-23
My desktop computer has Ubuntu installed on it's primary hard drive, but I didn't reformat my secondary hard drive since it was filled with mp3s that I didn't want to lose. Consequently I've kept that drive as NTFS and can read from it fine.

I however have a laptop computer running Windows XP Pro. Even though I can't write to the NTFS drive from Ubuntu, is there any way I can write to it from the XP computer over the network?

---

### Post by Phlosten on 2006-05-23
To enable read/write access to the hard drive for the network would be to enable read/write access for Ubuntu too, I would guess.
There are a few people setting up their NTFS partitions for read/write access these days. It seems the warnings about possible problems are falling quiet and more and more people are doing it. Perhaps there have been some advances in the driver to make it a much safer process? 
However this may only be in regard to Ubuntu Dapper as these these warnings were prominant with Ubuntu Breezy. 
Maybe do an upgrade to Dapper in just over a weeks time when its released officially and enable r/w access to the drive and setup samba to share it with your laptop.

---

### Post by kzutter on 2006-05-23
Your ultimate solution is to get the mp3's off of ntfs and onto a linux filesystem.
Since you have commited to linux on the desktop, then you need to go all the way.
"Half measures avail us nothing."

How much free space do you have on your primary drive vs. how much space is being taken by mp3s?

Do you have a DVD burner? Tape backup? spare drive lying around?

---

### Post by nanotube on 2006-05-24
[QUOTE=unnes]My desktop computer has Ubuntu installed on it's primary hard drive, but I didn't reformat my secondary hard drive since it was filled with mp3s that I didn't want to lose. Consequently I've kept that drive as NTFS and can read from it fine.

I however have a laptop computer running Windows XP Pro. Even though I can't write to the NTFS drive from Ubuntu, is there any way I can write to it from the XP computer over the network?[/QUOTE]
you cannot let xp write that ntfs partition over the network, without having ubuntu write to it as well. and if you are running breezy, that will screw up your ntfs partition. there is a driver called "captive" that can supposedly write ntfs safely, but i haven't tried it myself, so can't say much more about it. search around and find a howto on installing it, if you are interested.

otherwise, why not just suck off those mp3s over the network to the xp machine, then wipe and reformat that partition, and put the mp3s back on it over the network?

---

### Post by unnes on 2006-05-24
[QUOTE=kzutter]Your ultimate solution is to get the mp3's off of ntfs and onto a linux filesystem.
Since you have commited to linux on the desktop, then you need to go all the way.
"Half measures avail us nothing."

How much free space do you have on your primary drive vs. how much space is being taken by mp3s?

Do you have a DVD burner? Tape backup? spare drive lying around?[/QUOTE]

The drive in question is a 120GB drive, filled with mp3s (approximately 1600 full albums), so backing up my data would be no small feat. I do have a DVD burner, but I am not keen on burning 25-26 DVDs just to facilitate a reformat.

I guess I'll wait til the stable Dapper release, and install Captive or Paragon at that time so I can write to NTFS. Thanks to all who replied for your suggestions.

---

### Post by netztier on 2006-05-24
[QUOTE=unnes]I however have a laptop computer running Windows XP Pro. Even though I can't write to the NTFS drive from Ubuntu, is there any way I can write to it from the XP computer over the network?[/QUOTE]

Yes:
[LIST]
[*]hook up that harddrive to your XP box
[*]enable file sharing for the entire disk or a subdirectory of your choice
[*]access this share from Ubuntu as "Windows share" via **Places -> Connect to Server...** 
[*]username/password used for this access must match an existing Username/Password pair on the XP Box.
[/LIST]
Like this, you can get read/write access to that harddrive. 

Ubuntu is talking SMB/CIFS (Sever Message Block/Common Internet File System) to the XP machine, it does not need to know NTFS for that. 

It's up to the file server (yes, doing it this way turns your XP box into an - albeit simple - file server) to know how to access it's local filesystems. Typically, XP does not have much difficulty with NTFS ;-)

[COLOR="Silver"]This of course does not answer the question of how to convert that drive to a linux file system (ext3, reiser, etc...). Without any temporary tertiary storage method (another drive, DVDs, Laptops & Desktops primary drives) , I'm afraid, this is not going to happen. I do not know of any NTFS -> ext3 conversion tools. Anyone?[/COLOR]

kind regards

marc

---

