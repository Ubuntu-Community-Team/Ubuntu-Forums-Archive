---
title: "MPlayer as default?"
date: 2006-03-04
forum: General Help
---

### Post by iMick on 2006-03-04
Hi all, I have just installed Ubuntu successfully as my first foray into the linux world. I am coming from a fairly advanced knowlege of OSX and am suprised how similar the two are in many respects.

Anyway I have installed and setup mplayer successfully (used the OSX version for ages) but I would like to make it my default player instead of that awfull totem one. Is this easy to accomplish?

Thanks in advance.

---

### Post by rudiz on 2006-03-04
sudo apt-get remove totem

sudo apt-get install vlc

---

### Post by iMick on 2006-03-04
LOL i removed totem but it is still there!!!   JUST DIE!!! :D

---

### Post by poningru on 2006-03-04
just find a music file you want to use with mplayer as default, right click on it and go to properties, there should be an open with tab and select mplayer.

---

### Post by iMick on 2006-03-06
Thanks guys, I hate it when it is that simple :)

---

### Post by iMick on 2006-03-06
Any ideas why totem is still there after I ran sudo apt-get remove totem?

imick@ubuntu:~$ sudo apt-get remove totem
Password:
Reading package lists... Done
Building dependency tree... Done
Package totem is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
imick@ubuntu:~$

---

### Post by aysiu on 2006-03-06
How do you know Totem's "still there"?

---

### Post by iMick on 2006-03-06
Don't worry,  fixed it!  I'm learning fast finally :)

sudo apt-get remove totem-gstreamer

---

### Post by Sutekh on 2006-03-06
Its probably just the menu entry.  You can double check by issuing the command
```
totem
```and see if anything happens

Open up the **Application Menu Editor** in the **Applications** -> **System Tools** Menu and uncheck the entry for totem.

Edit: Guess its not the menu entry!

---

