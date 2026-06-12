---
title: "amarok killed fcc. How to get it back?"
date: 2006-01-23
forum: General Help
---

### Post by jazzgossen on 2006-01-23
I installed FirstClass 8 beta manually, by getting an RPM package, uncompressing it, and copying the files to the right places. This used to work, untli I recently installed amarok, via synaptic.

Synaptic said that to install amarok it would have to remove fcc (i.e. FirstClass). Stupidly, I disregarded this. Sure enough, now FirstClass crashes with an abort signal (signal 11), even though I uninstalled amarok via synaptic.

This may be a pretty long shot, but does anybody here know how to get FirstClass working again? Since it's not in the repositories, I don't know what dependencies that amarok ruined. (BTW, I find it really strange that synaptic knew about fcc at all after I installed it, since I did it manually).

---

### Post by o_fortuna on 2006-01-23
[QUOTE=jazzgossen]I installed FirstClass 8 beta manually, by getting an RPM package, uncompressing it, and copying the files to the right places. This used to work, untli I recently installed amarok, via synaptic.

Synaptic said that to install amarok it would have to remove fcc (i.e. FirstClass). Stupidly, I disregarded this. Sure enough, now FirstClass crashes with an abort signal (signal 11), even though I uninstalled amarok via synaptic.

This may be a pretty long shot, but does anybody here know how to get FirstClass working again? Since it's not in the repositories, I don't know what dependencies that amarok ruined. (BTW, I find it really strange that synaptic knew about fcc at all after I installed it, since I did it manually).[/QUOTE]
One thing you could do is redownload the RPM, open up a terminal (Applications-->Accessories-->Terminal) and do the following (assuming the RPM is on the Desktop):
```
sudo apt-get install alien
cd Desktop
sudo alien package_name.rpm
```
This will install the RPM package like a .deb file (usually), replacing all the necessary files automatically, so it should work. Maybe. I've never installed fcc, so I wouldn't know. :( Anyway, it's worth a shot...

---

### Post by jazzgossen on 2006-01-24
I tried to rebuild a deb package from the rpm pack, and used dpkg to install it. Neither alien nor dpkg gave me any error messages, but the problem remains. 

Is there any way to see from an rpm or deb file which packages it depends on?

---

### Post by gaminggeek on 2006-05-02
bump?

---

### Post by Harold P on 2006-05-02
Run it from terminal and post the output, maybe that could help.

---

### Post by gaminggeek on 2006-05-03
fcc: Received signal 11 (aborting)...
Aborted

---

