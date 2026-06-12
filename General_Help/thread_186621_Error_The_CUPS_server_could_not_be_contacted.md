---
title: "Error The CUPS server could not be contacted"
date: 2006-06-02
forum: General Help
---

### Post by CameronCalver on 2006-06-02
Hey i wanted to set up network printing so i decided to have a go at it myself before looking at the forums so i edited etc/cups/cupsd/browse.conf and /ports.conf and now when i click printing it gives the error the CUPS server could not be contacted so how would i reinstall cups or can some1 post the browse.conf and there ports.conf and there cupsd.conf plz  and i didnt meen to put it as kubuntu i am actually runnin gnome 

Cameron

---

### Post by tydaking on 2006-08-28
Did u ever get this fixed? If so, please share how you resolved it. I've run into what seems to be the same problem. Thanks.

---

### Post by wilberfan on 2006-08-28
> **tydaking said:**
> Did u ever get this fixed? If so, please share how you resolved it. I've run into what seems to be the same problem. Thanks.

DITTO!  :confused:

---

### Post by CameronCalver on 2006-08-29
Lol i feal wanted go to 
[http://www.ubuntuforums.org/showthread.php?t=180342](http://www.ubuntuforums.org/showthread.php?t=180342)
and see how you go but remember to read ever page becuase i make the mistake with editing the wrong config file i think but let me no how you go

---

### Post by muzzamo on 2006-09-03
I had this problem too. As it turns out, when following some guide on the net i had added the file /etc/cups/client.conf , which contained the IP of the cups server i wanted to connect to. This worked fine until the server no longer existed, in which case this error started popping up.

So simple solution was to remove /etc/cups/client.conf (by default the file isn't there). 

Hope that helps.. this is my first post on ubuntforums.org.

---

