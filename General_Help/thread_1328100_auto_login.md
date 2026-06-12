---
title: "auto login?"
date: 2009-11-16
forum: General Help
---

### Post by proevofanatik on 2009-11-16
i upgraded from kubuntu 9.04 to 9.10. but now i cant auto login. how do i do this?

---

### Post by fancypiper on 2009-11-16
Can you click: System -> Administration -> Login Screen?

---

### Post by proevofanatik on 2009-11-16
im on kubutu m8. its set out different from ubuntu

---

### Post by arnab_das on 2009-11-16
do the following:

System>Administration>Login Screen>Unlock (enter your password)

then selct the option: "Log in as"

Select your username.

thats it! :)

---

### Post by arnab_das on 2009-11-16
okay so here's the kubuntu way.

press alt+F2

type: 

```
 kdesu /usr/sbin/gdmsetup
```

now a window will open, go to the "security" tab and check the enable automatic login option and your username.

---

### Post by ChrischanM on 2009-11-19
Hey there,

same system, same problem. Some remarks:

1) If you use KDE 4 (and I suppose you do), then you have the command "kdesudo" instead of kdesu. It cost me quite a while to find that out! ;-)

2) I typed in the code of arnab_das (with kdesudo), a small window appeared and disappeared after a second.

3) There is an auto-login function in the system settings. I activated it and got the following error messages after a reboot, the "kubuntu" screen with the progress bar and quite a while a black screen: 
> Configuration file "/home/chrischan/.kde/share/config/knotifyrc" not writable. Please contact your system administrator.
and
> Configuration file "/home/chrischan/.kde/share/config/foorc" not writable. Please contact your system administrator.
and
> kstartupconfig4 does not exist or fails. The error code is 3. Check your installation.
After this the normal login screen followed.

I changed the permission of the first file to 700 - no change. The second file doesn't exist.

---

### Post by fancypiper on 2009-11-19
I would:
1. Check permissions.  Directories should be 755, files should be 600 or higher.  If you have to create a file manually, you can create it by:

touch /path/to/<filename>

2. Check ownership.  Everything in /home/<user> should be owned by <user>.

To change ownership of the entire directory:

chown -R <user>.<user> /home/<user>

---

### Post by ChrischanM on 2009-11-19
Hi fancypiper,

I did like you said but unfortunately without success.

The German Ubuntu forum suggested that the problem is probably related to the partition encryption. In fact, I agree to the encryption during the installation. Others removed the encryption and auto-login worked. Until now they didn't find a solution to have both encryption and auto-login.

More details here (German language): [http://forum.ubuntuusers.de/topic/autologin-funktioniert-nicht-kstartupconfig4-/](http://forum.ubuntuusers.de/topic/autologin-funktioniert-nicht-kstartupconfig4-/)

And a bug report, full of useful information: [https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/368061](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/368061)

---

### Post by Abadon125 on 2009-11-19
It may be a fairly round about solution but if you install the Gnome desktop and log in using that once and use their GUI to change the log in settings then change back to KDE as your default environment.  I don't know if that will work though, I am fairly new to ubuntu.

---

