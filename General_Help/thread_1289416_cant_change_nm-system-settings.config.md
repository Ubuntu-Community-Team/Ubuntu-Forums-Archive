---
title: "cant change nm-system-settings.config"
date: 2009-10-12
forum: General Help
---

### Post by Menelius on 2009-10-12
I tried to get my wlan usb to work for almost a day now. Its a long story, so I rather don t want to talk about what I was doing. 

The Problem:

I have to change the setting "managed" from "false" to "true in the nm-system-settings.config file. But I simply cant change it. If i use "edit" (rightclick in openoffice), i get this message: "Object not accessible. The Object cannot be accesst due to insufficient user rights." (WTF???? Ive got the administrator status!!!) Well i tried to replace it, but also that didnt work. I even tried to delete this damn file but I also wasnt allowd to do that. (shouldnt do it anyway but my anger isnt stoppable :-) ). I tried to change the permissionsettings on this file but everything stayd grey, not allowing me to change anything. 

I know its able to open and change this file. there Forums in which is said that its possible. 

many thanks for your help

menelius

---

### Post by mechro on 2009-10-12
In a Terminal type *gksudo gedit*. After entering your user password it will open the gedit text editor where you can browse and open the file.

You need to learn a bit more about user privileges and the sudo command...

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mechro on 2009-10-12
Oops, Sorry! you're on Kubuntu... try g*ksudo kate*.

:redface:

---

