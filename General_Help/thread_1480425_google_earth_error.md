---
title: "google earth error"
date: 2010-05-11
forum: General Help
---

### Post by luftadler on 2010-05-11
Hi all,

I have Google Earth installed globally under **/opt**  and every time i run the application it returns this error: 

```
Google Earth could not write to the current cache or My Places file location.
The values will be set as follows:

My Places Path: "/home/user/.googleearth"
Cache Path: "/home/user/.googleearth/Cache"
```It is possible to set this paths permanently and to get rid of this error?
Other ideas regarding this problem?


Regards,
Cristian

---

### Post by upbeat.linux on 2010-05-11
Sounds like a permissions issue. What are the current permissions for both folders? You can do "ls -la" at the command line.

Try changing the ownership on .googleearth to your user where user is your username:

```
sudo chown -R user:user /home/user/.googleearth
```

---

### Post by upbeat.linux on 2010-05-11
Paths are defined in GoogleEarthPlus.conf 

KMLPath=/home/user/.googleearth
CachePath=/home/user/.googleearth/Cache

---

### Post by luftadler on 2010-05-11
yes, I also think that is a permission problem
permission under [B]/opt

drwxr-xr-x  8 root   root   4096 2010-05-11 20:19 google-earth

[/B]permission under[B] /home

drwx------  4 vasile vasile   4096 2010-05-11 23:46 .googleearth
[/B]

---

### Post by luftadler on 2010-05-11
So, I've changed the permission for google-earth folder under opt to the default user and I get the same error + a blank screen for application.

---

### Post by dcstar on 2010-05-11
Installing using this method has no problems:

[https://help.ubuntu.com/community/GoogleEarth#make-googleearth-package](https://help.ubuntu.com/community/GoogleEarth#make-googleearth-package)

---

### Post by Gonzalo_VC on 2010-05-15
[COLOR="Navy"]I have upgraded from Hardy and Googleearth was not working.
I unistalled and re-installed (a new one, apparently) with Synaptic and got this messages:

sh GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.1.3535.3218...............................................................
setup.data/bin/Linux/amd64/setup.gtk2: /usr/lib/libc.so.6: version `GLIBC_2.8' not found (required by /lib32/libglib-2.0.so.0)
setup.data/bin/Linux/amd64/setup.gtk2: /usr/lib/libc.so.6: version `GLIBC_2.9' not found (required by /lib32/libglib-2.0.so.0)
setup.data/bin/Linux/amd64/setup.gtk2: /usr/lib/libc.so.6: version `GLIBC_2.11' not found (required by /usr/lib32/libcairo.so.2)
setup.data/bin/Linux/amd64/setup.gtk2: /usr/lib/libc.so.6: version `GLIBC_2.9' not found (required by /usr/lib32/libgio-2.0.so.0)
setup.data/bin/Linux/amd64/setup.gtk2: /usr/lib/libc.so.6: version `GLIBC_2.11' not found (required by /lib32/libpng12.so.0)
setup.data/bin/Linux/amd64/setup.gtk2: /usr/lib/libc.so.6: version `GLIBC_2.8' not found (required by /lib32/libselinux.so.1)

I was getting messages like that before.

I'm running Lucid 64 bits. 
Any clues on how to solve this and got Googleearth running smoothly?
[/COLOR]

---

