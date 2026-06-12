---
title: "Run programs from server"
date: 2010-08-23
forum: General Help
---

### Post by triunenature on 2010-08-23
Ok, basic situation, i have a server with 2.5T of hdd space, ram to boot, and a decent cpu.  I also have a desktop made about 8 years ago... with a 20G HDD.

The server runs, ubuntu server, the desktop runs, ubuntu desktop, (how normal...).  Anyway, i don't want to clog my desktop up with lots of programs, if they can be run from the server to save space.

Anyway to achieve this?

Programs i had in mind:
OpenOffice -> Full suit
Audacity
GIMP

and many more...

Thanks in advance!!!

---

### Post by aeiah on 2010-08-23
you could run them over vnc or ssh, but to be honest if you keep all your personal files on your server, you won't run out of space on your desktop unless you install every bit of software in the repository. 

you'll get better performance by mapping your documents, videos and music to nfs shares and having all software local, especially if you're wanting to record things with audacity.

---

### Post by surfer on 2010-08-23
i agree. you'd be better off just exporting your /home/ via nfs from the server and have all your personal files there. the 20G will be more than enough for programs.

---

### Post by triunenature on 2010-08-23
Yea, i do keep all my personal files on the server...

Ok, thanks for the tip.  Mind linking me to a page on how to export my /home directory to the server.

(note, both my desktop and the server have overlaping usernames .. go figure.)

So is there anyway, to just delete my home directory on my desktop, and link it to the server?  And would i need to have ssh running contently for this to work?  or what exactly am i doing?

---

### Post by eric_1982 on 2010-08-23
One other option is to use SSH to call the program to your deskop from the server.

An example would be 

ssh -X -C root@serverip firefox

This would call firefox from the server to your local machine. This could also come in handy if you were at work or school and wanted to get around a firewall policy. 

If you want to call another application you just need to find the command to call it. For example if you wanted to call gedit you would just replace firefox with gedit. 

ssh -X -C root@serverip gedit

---

### Post by triunenature on 2010-08-23
> **eric_1982 said:**
> One other option is to use SSH to call the program to your deskop from the server.

An example would be 

ssh -X -C root@serverip firefox

This would call firefox from the server to your local machine. This could also come in handy if you were at work or school and wanted to get around a firewall policy. 

If you want to call another application you just need to find the command to call it. For example if you wanted to call gedit you would just replace firefox with gedit. 

ssh -X -C root@serverip gedit

SWEET.  Thank you soo much.  That is exactly what i wanted!!!

Wow... did you know there are 199 packages required to install firefox?? (My server doesn't have a gui... maybe thats why..)

---

