---
title: "How do I automatically file sync on laptop and desktop."
date: 2010-05-03
forum: General Help
---

### Post by Morganman on 2010-05-03
Hi
I have updated to 10.04 on my desktop and on my Dell Inspiron 8200 laptop.
What I would like to do is have the machines automatically synchronise working files as they change on each machine. I have found backup programs but am not sure if they will do what I need. 

Has anybody achieved this? If so could you please advise me.

Many Thanks

---

### Post by parn on 2010-05-03
Add both machines to ubuntu one and synchronize the folders you wish. You get 2GB of online space for free above that you have to pay.

---

### Post by Morganman on 2010-05-03
That's not really an option I want to use.
Prefer to use my own network.

Thanks For Response

---

### Post by rhodry on 2010-05-03
For true sync as distinct from file backup/share I have used:

unison-gtk
a file-synchronization tool for Unix and Windows with GTK+ interface

It works fine & it is in the repos.

Alternatively; create a common partition for shared data files (not /home, rather things like music, videos & documents) & mount it on each system through /etc/fstab. Create links from respective /home folders. eg:

common folder = /data/music

/home/user1/music is dynamic link to /data/music
/home/user2/music is dynamic link to /data/music

Get the picture?

Rhodry.

---

