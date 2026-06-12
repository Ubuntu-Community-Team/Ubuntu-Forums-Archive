---
title: "Directory writable"
date: 2010-05-06
forum: General Help
---

### Post by rflores2323 on 2010-05-06
Need help to make a folder writable

I downloaded and put the folder directory XWMM into a folder: 

usr/share/xbmc/web/XWMM


I logged in as root by:
     Code:
     sudo nautilus 
and changed the permissions on all the folders,  to Read ALL,
Write ALL and Execute ALL.

I save it and then go back in to see if my changes were saved and nothing saved.


Am I doing something wrong, far as setting the permissions?
Do I need to type something in the terminal, to set the permissions? like chmod 777 or something like that?  

Do not know terminal commands so if someone could provide me with the command that would be great. (newbie)


Any help would be greatly appreciated.

---

### Post by rflores2323 on 2010-05-06
anyone

---

### Post by tgm4883 on 2010-05-06
try 

gksudo nautilus

---

### Post by tgm4883 on 2010-05-06
Also, 'sudo chmod 777 DIRNAME' would work too, but is pretty open (as anyone can write to that directory)

---

### Post by rflores2323 on 2010-05-06
i have tried the below but nothing

xbmc@xbmc-desktop:~$ sudo chmod 777 web
chmod: cannot access `web': No such file or directory
xbmc@xbmc-desktop:~$ sudo chmod 777 /web
chmod: cannot access `/web': No such file or directory
xbmc@xbmc-desktop:~$ sudo chmod 777 /xbmc/web
chmod: cannot access `/xbmc/web': No such file or directory
xbmc@xbmc-desktop:~$

---

### Post by tgm4883 on 2010-05-06
you would need to use the full path (or be in a directory right above it)

usr/share/xbmc/web/XWMM

---

### Post by rflores2323 on 2010-05-06
thanks got it.

---

