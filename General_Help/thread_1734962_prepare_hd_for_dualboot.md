---
title: "prepare hd for dualboot"
date: 2011-04-20
forum: General Help
---

### Post by hilemb1 on 2011-04-20
Just given a laptop with xp installed.I want to dualboot BUT my hd defragger shows bits of the xp os spread out over the entire drive so I can't partition without making xp corrupted.Is there any way to move the xp bits as to make a clean space on the hd to partition for ubuntu.I wouldn't mind wiping the drive and reinstalling xp to get a clean space to partition but I hate the time wasted for all the windows updates.

---

### Post by oldfred on 2011-04-20
Welcome to the forums.

With XP you can just use gparted and it will move the files. Always have good backups, but it works. Most errors are power failure in the middle of editing partitions or user (I had done that too).

Defrag a couple of times speeds up the process but is not essential. Windows works better if it has at least 20% free space in the NTFS partition.

Installs -----------------------
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by hilemb1 on 2011-04-21
Is that gparted the live cd or gparted in the ubuntu live cd?

---

### Post by vuetrip on 2011-04-21
gparted is on the ubuntu live CD in System -> Administration -> Gparted partition Editor

---

### Post by oldfred on 2011-04-21
I have used both. If Ubuntu liveCD is older then download the newest gparted liveCD. I like to have several rescue CDs. I used to have a bunch of CDs but keeping them updated was always an issue. I have now converted to using USB flash drive and multiboot the ISOs on it.

---

### Post by hilemb1 on 2011-04-21
Thanks to everyone for the good info and the quick replies.Solved my problem in a very interesting way.Here's the story. 
 Went to the public library to check on the gift Inspirons' wireless as I'm only wired to broadband at home.Sat next to a lady with a X301 Thinkpad and we started to talk.She said that she hated the small glossy screen on her Thinkpad and wanted a larger matte screen."Want to trade?" she asked.I told her the Thinkpad was a much more expensive and powerful laptop but she didn't care.So now I have an X301 Thinkpad for free.
 Will use your info on the Gparted live cd to prepare the hd for dual boot my former primary laptop.What a great day!
 Have another question if it's allowed on this thread.Using portable Ubuntu remix on a thumb drive.It's 9.04 and on the update manager it says I can update to 10.10.Ever tried it? The remix uses Cygwin and has no gnome desktop so will I screw it up?

---

