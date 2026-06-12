---
title: "Weird partition mount problem"
date: 2010-09-28
forum: General Help
---

### Post by aeronutt on 2010-09-28
Ok, so I have some weird issues popping up since I installed 10.04. And I think I'm on to something.  I have a 99GB partition, sda8, that I use for most of my data files. Odd thing is, sometimes when I use the 'places' menu and open up '99GB', it actually goes to my home directory on sda4...and sometimes it goes to sda8. Some other weird things happen also. But here's what I noticed, even when sda8 isn't mounted, there's an sda8 in /media; that is, there's an /media/sda8.  Here's one thing I looked at, I did an 'ls -l' with sda8 mounted, and with sda8 unmounted, here's what I see:

with sda8 unmounted, an ls -l in /media shows:
drwxr-xr-x 2 root root 4096 2010-09-27 16:38 sda8

with sda8 mounted, an ls -l in /media shows:
drwxrwxrwx 5 root root 4096 2010-01-24 16:42 sda8

Any clues as to why an sda8 is showing up in /media, even though sda8 isn't mounted?????

When I cd to /media/sda8 (when unmounted), it's empty.

---

