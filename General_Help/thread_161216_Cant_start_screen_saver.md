---
title: "Cant start screen saver"
date: 2006-04-16
forum: General Help
---

### Post by hydric on 2006-04-16
Got many problems. Really new to ubuntu (5 days) so plz bear with me 

1) I cant start my screen saver. It tries to start the xscreenserver by its self but shows an error message saying something about my access control being turned on. (i'am running as root). its says to type:
                         xhost +localhost
which i did, but still no luck....................... ](*,) 
please help.

2) I have mounted my windows partitions using fstab in the /mnt directory. I have no problems accessing those folders as root, but when i loog on using my general account, it says premission denied. i tried to use chmod (as root), but since the partitions are  NTFS it says "read only drive". How do i allow all users to acces the mounted folders.

---

### Post by Ramses de Norre on 2006-04-16
Mount them with a line similar to this in your /etc/fstab (sudo gedit /etc/fstab and add line at the bottom):```
/dev/hda2       /media/hda2  ntfs    nls=utf8,umask=0222 0       0

```change device (/dev/hda2) and mountpoint (/media/hda2) to your needs.

---

### Post by harisund on 2006-04-16
[QUOTE=hydric]Got many problems. Really new to ubuntu (5 days) so plz bear with me 

1) I cant start my screen saver. It tries to start the xscreenserver by its self but shows an error message saying something about my access control being turned on. (i'am running as root). its says to type:
                         xhost +localhost
which i did, but still no luck....................... ](*,) 
please help.
[/QUoTE]

Ok a couple of things

1. Make sure your screensaver daemon is indeed running. You can do this by running ```
xscreensaver-demo
```. If the daemon is not running, it will prompt you to start it. You can click on yes (generally it will be running, atleast on a default install. it will be stopped only if you had specifically stopped it)
2. next, in that window you can choose the different screen saver options. 
3. If you are impatient, and you want to immediately start your screensaver, run ```
xscreensaver-command -activate
```. If you want to lock your screen down (like if you are leaving for a quick errand and don't want anyone snooping around) you should run ```
xscreensaver-command -lock
```. This will both activate your screensaver and lock the screen too. 
4. If you are using a laptop and just want to shut the screen down (no screensaver. Just plain switch off) you should use ```
xset dpms force off
```

And no, you don't need root permission. What you do need are the permissions of the user currently accesing the screen, which invariably is yourself.

Hope that helped.

---

### Post by hydric on 2006-04-20
[QUOTE=harisund]Ok a couple of things

1. Make sure your screensaver daemon is indeed running. You can do this by running ```
xscreensaver-demo
```. If the daemon is not running, it will prompt you to start it. You can click on yes (generally it will be running, atleast on a default install. it will be stopped only if you had specifically stopped it)
.[/QUOTE]

OK i did that. After clicking yes, i get the following error:
> 
The xscreensaver daemon did not start up properly.
You are running as root.  This usually means that xscreensaver
was unable to contact your X server because access control is
turned on.  Try running this command:
xhost +localhost
and then selecting `File / Restart Daemon'.

(etc etc................>)



which i did. and then got the same error ..................... :roll:

---

### Post by harisund on 2006-04-20
I am really sorry, I am afraid I can't help you out much there.. I wouldn't advise you to run in root mode .. but I don' know how to fix that error..

---

### Post by hydric on 2006-04-21
hey no probs. Every one i know advised me to switch to a general user anyways.
and thanks for trying............

---

### Post by Rastareefer on 2006-06-26
Screen savers will not run in Kubuntu 6.06 or Suse 10.1 with the KDE desktop, either.
They did run on the initial instalation of Suse but stopped after doing the sytem updates. The power thing also seems to be related to this problem from what I have found when searching for a fix. Not that I have found one yet.](*,)

---

