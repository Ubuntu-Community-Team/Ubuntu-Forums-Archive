---
title: "Proper way to use temp file and or /tmp in bash script"
date: 2011-04-25
forum: General Help
---

### Post by InkyDinky on 2011-04-25
I'm wondering if there is a proper way (or just best practice) to using temp files and the /tmp directory.

Background story:
In  a script I had been using mktemp to create temp files in /tmp.
Needless to say that after running this script for a while, it filled /tmp and my HDD with these files. I didn't realize that i needed to do house cleaning of /tmp.

So now I'm curious as to how to properly use temp files and how to not abuse /tmp.  
I suppose some of my shortcomings arise from the fact that I somehow had the crazy idea that /tmp was policed by the system and cleaned out when necessary.
I assume that I'll just need to self police and use my temp files more intelligently and get rid of them when I'm done with them instead of letting them clutter up /tmp.
Is this all I need to look out for or am I missing something?

---

### Post by Rinzwind on 2011-04-25
I would not use /tmp/ but either in a dir in the home of the user or /var/tmp or /usr/tmp/ (last 2 are OS dependent).

If need be you can write a small cron-script that cleans your ./tmp/ every boot or every x-hours. But I would advice doing so in your script itself. That way you can have a section cleaning your tempfiles in your software and do not need a seperate script.

edit:
sample from the web regarding temp files:
[https://www.infosecisland.com/blogview/10055-Using-Temporary-Files-in-Linux-Scripts-Securely.html](https://www.infosecisland.com/blogview/10055-Using-Temporary-Files-in-Linux-Scripts-Securely.html)
- take attention to one of the advices here: make sure you set the lowest possible rights on the file.

Oh and the BEST option is to not use temp files at all ;)

---

### Post by lithopsian on 2011-04-25
/tmp is policed by the system and cleaned out ... when you reboot!

---

### Post by DaithiF on 2011-04-26
Hi, on debian/ubuntu tmp is cleaned on boot, there is a setting in the /etc/default/rsS file TMPTIME which gives the age of the files to delete (the default is 0 on 10.10, ie. everything gets deleted).

on redhat systems there is a different approach -- a daily cron job which does the deleting.

Sounds like your system remains up for long periods, in which case you may wish to disable the on boot cleaning and implement a redhat-like cron script instead.  Setting the TMPTIME variable to a negative value will turn off the on-boot cleaning out of /tmp.  Then put a script into /etc/cron.daily to delete files in /tmp older than some threshold

---

