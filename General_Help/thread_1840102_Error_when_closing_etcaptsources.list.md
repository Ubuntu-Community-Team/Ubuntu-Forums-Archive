---
title: "Error when closing /etc/apt/sources.list"
date: 2011-09-06
forum: General Help
---

### Post by hydrotyler on 2011-09-06
Hey everybody, I am new to Ubuntu and would like some help resolving an annoying error I keep getting when I close my sources list.  I am calling the sources list with gksudo gedit /etc/apt/sources.list with no problems, but when I save a change made, or close the window I get this error:

(gedit:4763): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:4763): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.ABF90V': No such file or directory


I would like to fix this, or figure out why it is happening. Thanks for your help!

---

### Post by hydrotyler on 2011-09-06
Hey everybody, I am new to Ubuntu and would like some help resolving an  annoying error I keep getting when I close my sources list.  I am  calling the sources list with gksudo gedit /etc/apt/sources.list with no  problems, but when I save a change made, or close the window I get this  error:

(gedit:4763): Gtk-WARNING **: Attempting to set the permissions of  `/root/.local/share/recently-used.xbel', but failed: No such file or  directory

(gedit:4763): Gtk-WARNING **: Attempting to store changes into  `/root/.local/share/recently-used.xbel', but failed: Failed to create  file '/root/.local/share/recently-used.xbel.ABF90V': No such file or  directory


I would like to fix this, or figure out why it is happening. Thanks for your help!

---

### Post by Quackers on 2011-09-07
Is this in Ubuntu 11-04?
I had this problem and fixed it by running this in the terminal
```
sudo mkdir -p /root/.local/share
``` Once that's run re-open the sources.list and then save the file again. The error message should disappear.

---

### Post by Quackers on 2011-09-07
See other thread.

---

### Post by hydrotyler on 2011-09-07
That makes sense to make the directory. I tried and it worked. Thank you!

---

### Post by Quackers on 2011-09-07
You're welcome :-)
I have used different iso's of 11-04 and I have to run that command on every one of them. I have no idea why that directory is not created by default. I'm sure it should be.

---

### Post by yetiman64 on 2011-09-07
> **Quackers said:**
> You're welcome :-)
I have used different iso's of 11-04 and I have to run that command on every one of them. I have no idea why that directory is not created by default. I'm sure it should be.

I think it is because with the root account being locked in Ubuntu by default it may not be seen as necessary by the devs. The root folder structure involving the graphical environment is normally not used like the users account (other distros would no doubt create this setup that use the root account for graphical root logins).

Good simple fix that though, will need to remember it, have just ignored those errors in the past myself as they do no harm. :)

---

### Post by Quackers on 2011-09-07
The fix was originally suggested by MacUntu - thanks to him :-)

What I was finding was that the edited file would not be saved and the edit did not take effect until that file was created.
Don't you have the same problem yetiman64?

---

### Post by yetiman64 on 2011-09-07
No, I've seen those errors regularly since 7.10 using the command gksu (or gksudo) gedit or in particular nautilus, never had a problem saving, deleting or generally altering a file though with either command. 

Probably why I got the idea it was related to the locked root account and could be ignored. Though if problems occur setting that folder structure up does make sense.

Edit: I currently don't have an 11.04 install but have had in the past and don't recall any problems even in it. :-k

---

### Post by Quackers on 2011-09-07
Thanks yetiman64, but the info I gave was not correct!
My problems have happened with Ubuntu 11-10 only, not 11-04, which is fine. My bad!

---

### Post by lisati on 2011-09-07
Threads merged.

---

### Post by hydrotyler on 2011-09-12
Well, either way it fixed my problem. Spotify was actually what created the problem to begin with if I recall correctly. Thanks again.

---

