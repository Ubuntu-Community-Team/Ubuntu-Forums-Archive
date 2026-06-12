---
title: "Possibile nautilus bug"
date: 2010-02-08
forum: General Help
---

### Post by tzily on 2010-02-08
Hi, I just thought I should signup, been checking this forum for a while  and so far it had answered most of my google searches.
I'm on Karmic Ubuntu and this problem keeps annoying me since it will  probably damage my hdd. It's like this:
I seed a lot of torrents and I'm keeping my external plugged in; most of  the time it's innactive since no one is leeching old torrents and it  stays mounted in stand by, being a LP model. 
Now, whenever I access a folder on my desktop to browse or whatever,  Nautilus freezes because it takes time to get my external back from the  stand by. The problem is that the desktop folder isn't linked in any way  to the external, so why is Nautilus refreshing everything including my  externals when it gets started ? I have 3 externals and this happens for  them all.
Did you guys ever experienced this ? I was wondering if there was a fox  around this or something, I'm kinda new to linux graphic interfaces....  Thanks.

---

### Post by dearingj on 2010-02-08
I've never noticed this problem with my external drives (identical Maxtor drives; I'll find their model number asap). Let's try to narrow things down a bit:
1) Have you tried accessing your desktop [using a terminal]("https://help.ubuntu.com/community/UsingTheTerminal")? Perhaps try opening a terminal (Applications->Accessories->Terminal) and entering:
```
cd ~/Desktop # Change directory into your desktop
touch testfile # this will create an empty file, just to see if it causes your external to come out of standby
rm testfile # Removes the test file we just created
```

2) Try installing a different file manager such as [Thunar]("apt:thunar"). See if Thunar can access that folder on your desktop without having to wait for the external drive.

---

### Post by tzily on 2010-02-08
The terminal method works fine and it doesn't start the hdd ...
I guess I'll have to try Thunar, thanks

---

