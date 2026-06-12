---
title: "Automatically connect to a Windows partition"
date: 2009-09-22
forum: General Help
---

### Post by xxmatt3232xx on 2009-09-22
Hi there, I am dual booting Windows Vista and Ubuntu 9.04 (with windows as the primary OS).

Here is the problem, all my music and movies are still on the Windows partition and I would like to have Ubuntu automatically connect to the Windows partition when it starts up so that when I open Rhythmbox it will not begin removing all my music.

Everything is fine as long as I manually browse to the windows partition before opening Rhythmbox, its just slightly annoying and Im sure there is a simple way to fix this.

the path to my music is: "/media/OS/Users/Matt/Music/iTunes/iTunes Music"

Thanks for the help.

---

### Post by mac9416 on 2009-09-22
I believe you have to edit /etc/fstab to include the Windows partition. The process is explained here: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
That page also mentions a GUI method using something called pysdm, but I have no experience with that.

Good luck
-mac

---

### Post by xxmatt3232xx on 2009-09-23
I got it working with pysdm, it changed the directory from /media/OS/... to /media/sda3/OS/... so all I had to do was change the music directory in Rhythmbox.

Thanks for the help

---

