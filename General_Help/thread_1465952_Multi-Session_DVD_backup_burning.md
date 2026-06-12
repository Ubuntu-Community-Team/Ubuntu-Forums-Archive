---
title: "Multi-Session DVD backup burning?"
date: 2010-04-29
forum: General Help
---

### Post by Sickofwindows70 on 2010-04-29
Is there any way to save data to a DVD & leave the disk "open" to add files after the session is closed? I like to backup my MP3 files to DVD's, been doing it for years using Windows Vista. As I collect more MP3's I add em to the same DVD. Can't do this using Brasero or any other program I have tried - once I write a file the disk is closed.

---

### Post by ellgor on 2010-04-30
Hi,

Yes you can, with K3b but not with a current edition, it has to be 1.0.5 which can be found here:

[http://packages.ubuntu.com/jaunty/libk3b3](http://packages.ubuntu.com/jaunty/libk3b3)
[http://packages.ubuntu.com/jaunty/k3b-data](http://packages.ubuntu.com/jaunty/k3b-data)
[http://packages.ubuntu.com/jaunty/k3b](http://packages.ubuntu.com/jaunty/k3b)

install them in that order as some dependencies are still needed, also if you have K3b already installed, remove it first, and this is to stop the updater from trying to update to a newer version:

In a terminal type

sudo gedit /etc/apt/preferences
and enter


Package: k3b
Pin: version 1.0.5*
Pin-Priority: 1001

Package: k3b-data
Pin: version 1.0.5*
Pin-Priority: 1001

And that should do it.

Regards, Ellgor.

---

### Post by psusi on 2010-04-30
You are using actual DVD-R instead of rewritables?

---

### Post by johnbrown105 on 2010-05-10
> **ellgor said:**
> Hi,

Yes you can, with K3b but not with a current edition, it has to be 1.0.5 ...

Do you know if this has been fixed in Kubuntu Lucid? I am running Lucid and I cannot burn multisession DVDs. I get an "unknown error", but maybe I have already spoilt my blank DVD-R disk, although k3b says that it is empty with 0 sessions.

---

### Post by ellgor on 2010-05-11
Hi,

psusi is correct, DVD-R, change to DVD+R and it will work.

Regards, Ellgor.

---

### Post by cap10Ibraim on 2010-05-11
I actually do this with CD-R not RW 
in Ubuntu > brasero disc burner , you can do this ,first burn choose keep the CD open for multi-session then on the second burn choose to import data
I use nero on windows 
anyway I think the brasero import option don't give you any advantage , I noticed that it copy the old data and burn them again with the new data in a new session ,(old data will be duplicated)
yesterday I faced a similar problem [Check the Thread]("http://ubuntuforums.org/showthread.php?p=9277955#post9277955")

---

