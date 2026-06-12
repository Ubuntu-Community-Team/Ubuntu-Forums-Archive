---
title: "User can't log in"
date: 2010-01-16
forum: General Help
---

### Post by nervous137 on 2010-01-16
Hi
I am using Ubuntu 9.10. I currently have two users myself and my wife.
Yesterday morning when I tried to log in I receive the following messages
"Could not update ICEauthority file /home/david/.ICEauthority"
then
"There is a problem with configuration server /usr/lib/libgonf2-4/gconf-sanity-check-2 with status 256"
and finally
"Nautilus could not createthe following required folder /home/david/Desktop/.nautilius"

I searched the forum and followed some stuff about chmod 755 for the gconf file etc but still have the same problem.
I would be grateful for any help. My wife can still log in with no problem by the way.

TIA

D

---

### Post by mechro on 2010-01-16
Using the LiveCD or possibly your wife's session, delete /home/david/.ICEauthority and reboot.

---

### Post by nervous137 on 2010-01-16
Thanks for the quick reply, there isn't a .ICEauthority file (I am viewing hidden files)

D

---

### Post by bsh on 2010-01-16
disk full? you have quota and used it up? someone changed permissions on your home folder?

---

### Post by prshah on 2010-01-16
> **nervous137 said:**
> 
"Nautilus could not createthe following required folder /home/david/Desktop/.nautilius"

Looks to me like for some reason your  home folder is inaccessible or absent; to confirm, can you post back the outputs to the following terminal (Applications-Accessories-Terminal) commands: (Please obfuscate filenames as per your preference)```
ls -ld /home/*
ls -l /home/david
``` You can run these commands from your wife's user ID.

---

### Post by mechro on 2010-01-16
@ nervous137

Does Ubuntu 9.10 have an option to log in to a failsafe Gnome session?

---

### Post by nervous137 on 2010-01-16
Thanks for your help here
Below are the responses to the commands you asked me to input.

emily@ubuntu:/home/david$ ls -ld /home/*
dr-x------  5 emily david 4096 2010-01-16 11:31 /home/david
drwxr-xr-x 38 emily emily 4096 2010-01-16 11:44 /home/emily
emily@ubuntu:/home/david$ ls -ld /home/david
dr-x------ 5 emily david 4096 2010-01-16 11:31 /home/david
emily@ubuntu:/home/david$

---

### Post by sisco311 on 2010-01-16
Your home directory is owned by your wife. :)

run:
```

sudo chown -R david\: /home/david
sudo chmod 0750 /home/david 
sudo chmod 0644 /home/david/.dmrc
```

For more details check out: [thread=976610]Solving .dmrc and $HOME Permission Errors[/thread]

---

### Post by mechro on 2010-01-16
> **sisco311 said:**
> Your home directory is owned by your wife. :)



What's unusual about that? My nuts are owned by my wife! ;)

---

### Post by nervous137 on 2010-01-16
Mmm thanks. I don't have a .drmc file (I am viewing hidden files), can I create one?

Thanks

D

---

### Post by sisco311 on 2010-01-16
> **nervous137 said:**
> Mmm thanks. I don't have a .drmc file (I am viewing hidden files), can I create one?

Thanks

D

Well, I don't have it either. Don't worry about it. If it's needed, the system will recreate it.

---

### Post by nervous137 on 2010-01-16
Great I own my own Home folder again, many many thanks to all who supplied suggestions, and helped resolve this issue for me.

D

---

