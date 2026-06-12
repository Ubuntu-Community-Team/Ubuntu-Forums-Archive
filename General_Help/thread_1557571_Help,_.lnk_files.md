---
title: "Help, .lnk files"
date: 2010-08-20
forum: General Help
---

### Post by nzracing980 on 2010-08-20
Hey guys,

so i have got a VPS Virtual Private Server that i have broght overseas and i am willing to host a few files e.g. a game file (dedicated game server)

I use "putty and tightvnc viewer" to remote desktop to my VNC.

Now this is a windows application,

I have ubuntu 9.10 and also have wine.

I have uploaded all the files to the win c: programs files, folders.

BUT! When i went to upload my windows shortcut (.lnk) file, i placed it on my desktop, i went to right click on it and open with wine and it said,
(picture displayed at bottom of what it said)

ALSO i am having trouble with typing in the VPS, for exapmle when i type the letters "qwerty" on my laptop keyboard it come up with messed up keys like e.g. "c.ajsn" or something,

Can someone help me out with both of these?

Cheers

---

### Post by tg3793 on 2010-12-10
Yup, I and a lot of other people have had this same sort of problem. Here are the resources I and other have dug up on it so far.


[http://brainstorm.ubuntu.com/idea/14361/](http://brainstorm.ubuntu.com/idea/14361/)
[http://freshmeat.net/projects/outwit/](http://freshmeat.net/projects/outwit/)
[http://bugs.kde.org/show_bug.cgi?id=85348#c7](http://bugs.kde.org/show_bug.cgi?id=85348#c7)

I've put several hours in trying to fix this problem; including trying to get a share working in a WindowXP virtual box. Nothing exciting to report yet. Someone please let me know if you come up with a good solution for this that would apply to Ubuntu 10.04 Lucid. Thanx.

---

### Post by tg3793 on 2010-12-13
Ok; fifteen hours of researching this problem and working on this problem and I finally stumble on the fact that this is built into WINE. It's working great for me and if anyone wants to find out how I did it they can [click here]("http://techsupporttv.wordpress.com/2010/12/14/following-lnk-files-windows-shortcuts-in-ubuntu/").

I really think this will help a 'ton' of people.

---

