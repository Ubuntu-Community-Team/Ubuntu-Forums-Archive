---
title: "vlc media player"
date: 2006-04-13
forum: General Help
---

### Post by Gaia on 2006-04-13
Hi,

I've searched the forums but couldn't find what i was looking for.

How do you install VLC media player? It doesn't have Ubuntu listed in it's downloads section but i've read that people can use it with Ubuntu?

Thanks.

---

### Post by Jedeye on 2006-04-13
open up the Terminal
```
sudo apt-get install vlc
```

---

### Post by Gaia on 2006-04-13
[QUOTE=Jedeye]open up the Terminal
```
sudo apt-get install vlc
```[/QUOTE]

Hi,

Thanks, but it says that the package cannot be found?

---

### Post by nastavirss on 2006-04-13
install vlc
-----------------
Code:
first, edit your sources.list by:
Code:
sudo kwrite /etc/apt/sources.list
and uncomment (fancy word for removing the # signs) the lines starting with deb. It should now look like:
Code:
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
Now, run
Code:
sudo apt-get update
and
Code:
sudo apt-get install vlc
Now, if you want a better looking front-end (not that the default is ugly, but some people are impressionate)
Code:
sudo apt-get install qvlc

---

### Post by Gaia on 2006-04-13
hey,

It says that kwrite is not a correct command and when i changed it to write it says that /etc/... is not logged in.

Thanks.

---

### Post by drewbie on 2006-04-13
try 

sudo gedit /etc/apt/sources.list

---

### Post by nastavirss on 2006-04-13
u can use "vi" or "gedit"

---

### Post by NoWhereMan on 2006-04-13
you can add sources from synaptic as well. also, look at [http://nightlies.videolan.org](http://nightlies.videolan.org)

---

### Post by Gaia on 2006-04-13
ah thanks all, worked perfectly!

---

