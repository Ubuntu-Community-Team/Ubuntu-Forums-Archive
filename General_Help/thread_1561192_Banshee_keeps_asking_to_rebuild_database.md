---
title: "Banshee keeps asking to rebuild database"
date: 2010-08-25
forum: General Help
---

### Post by nebcanuck on 2010-08-25
Hi there,

I am trying to use Banshee to sync my 5th generation iPod nano on a Lenovo laptop. When I plug the iPod in, it is recognized just fine by Banshee, however when I click on the iPod icon it tells me that it is unable to read the iPod because it has been used with a version of iTunes that saves a version of the database that Banshee can't recognize.

All of this is fine. I click on rebuild iPod database since I have no intention of using iTunes in the future with this iPod, and I don't mind losing the playlists or songs on the iPod (I have them all on the computer). The database rebuilds normally from all appearances, and after a short time I am able to read all songs on the iPod and transfer things back and forth.

The frustration comes into play with the fact that next time I load up the iPod on Banshee, it asks for the exact same process. It is unable to read the iPod, needs to rewrite the database, etc..

Is there some way to permanently alter the database that I'm missing, or is this an issue with 5th generation compatibility? Sorry if there's an easy fix that I just haven't been able to find online.

---

### Post by nebcanuck on 2010-08-28
Okay, so this iPod situation has gone from bad to worse.

I thought after some initial consideration that Banshee simply wasn't making any changes to the iPod at all. So I looked to other programs like gtkpod to see if I could get some music properly sent over. What I began to realize was that, in fact, these programs (including Banshee) were writing to the iPod, but the iPod was not recognizing the changes. Perhaps because the database was still not being altered?

I attempted via other Ubuntu Forum suggestions to wipe out the iPod's iPod_control file to wipe the iPod's database and music and start from scratch. This worked, however even now when I write songs to the iPod they are not recognized by the actual iPod interface.

To boot, the iPod now seems to only have half of the space it started with, claiming to have 3.6 GB free when it's an empty 8 GB iPod!

So here comes the big question: Is there a program on Linux which can allow you to restore your iPod as you can in iTunes? If not, is there a way to get iTunes to restore your iPod running under either Wine or Virtualbox? If not, is there a way to use gparted to format the iPod's filesystem, since it does not seem to recognize HFS off the bat?

---

### Post by karel2009 on 2010-08-28
If you have your music backed up than you can reformat the ipod to fat32  (gparted is a good choice) and use gtkpod to create the ipod  file/directory structure. Than use gtkpod to copy all the music you  want.

Let me know if you need more help.

---

### Post by nebcanuck on 2010-08-30
Sounds good, but gparted doesn't recognize the iPod currently. Running under the terminal, I get this report:

> Device /dev/sdb has a logical sector size of 4096.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.

Ignoring device /dev/sdb with logical sector size of 4096 bytes because gparted only supports a size of 512 bytes.

Will search for an answer, but if there's an easy one that you know of it would be appreciated. Will post if I make progress.

---

### Post by nebcanuck on 2010-08-30
Compiled the most recent version of gparted and successfully formatted the iPod. Now trying GTKpod to build the database.

---

### Post by nebcanuck on 2010-08-30
GTKpod and Banshee now both recognize the iPod. It is back to normal memory amounts. However, the initial problem doesn't seem to have been resolved.

As it stands, I can add files to the iPod, and both Banshee and GTKpod recognize that the files are there. If I browse the iPod in nautilus, they are indeed under the iPod_Control/Music folder. However, the iPod itself does not recognize that it has any music on it. It says there are zero songs when I go to play something.

So, back to square one. Why does my system not seem to work with my iPod?

---

### Post by JedV on 2010-08-31
:(  I had the same symptoms with my iPod Nano 8gb (5th Generation) that I bought yesterday.  Banshee couldn't sync the songs in a way that the Nano would read.

I tinkered with Virtualbox and ended up not having luck.  iTunes wouldn't install cleanly, and crashed when I tried to run it in my WinXP (guest) environment.  I was able to get my iPod to be recognized in the virtualbox session, but somehow the iPod was set into a read-only mode.  

I took it to a friends place with my music on a flash drive and ran iTunes from a proper WinXP box.  Lame, I know... but everything works now.

---

