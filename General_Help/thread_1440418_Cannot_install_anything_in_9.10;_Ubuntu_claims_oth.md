---
title: "Cannot install anything in 9.10; Ubuntu claims other software managers are running."
date: 2010-03-27
forum: General Help
---

### Post by alien5p5g on 2010-03-27
Hi,

I was having issues installing anything from the software center. It claimed that other software managers were running (and as far as I can tell, none were)

I could also not install anything from any other package installer.

I went into Synaptic and it told me to run this command:

```
sudo dpkg --configure -a
```

I did, only to see this result:

```
Setting up libmatroska0 (0.8.1-1.1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmatroska0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libsdl-image1.2 (1.2.7-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libsdl-image1.2 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libqtcore4 (4.5.3really4.5.2-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqtcore4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmpcdec3 (1:1.2.2-2.1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmpcdec3 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up liblua5.1-0 (5.1.4-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing liblua5.1-0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libpostproc51 (4:0.5+svn20090706-2ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libpostproc51 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmpeg2-4 (0.4.1-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmpeg2-4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libiso9660-5 (0.78.2+dfsg1-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libiso9660-5 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmad0 (0.15.1b-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmad0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmodplug0c2 (1:0.8.7-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmodplug0c2 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libqtgui4:
 libqtgui4 depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqtcore4 is not configured yet.
dpkg: error processing libqtgui4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libmatroska0
 libsdl-image1.2
 libqtcore4
 libmpcdec3
 liblua5.1-0
 libpostproc51
 libmpeg2-4
 libiso9660-5
 libmad0
 libmodplug0c2
 libqtgui4

```

And the problem was not fixed. It seems as though that was supposed to fix it because when I googled the issue, people seem to have no problems afterwards. :-/

---

### Post by alien5p5g on 2010-03-27
Sorry for a double post, but I need help. :/

---

### Post by spiderbatdad on 2010-03-27
maybe this:
```
sudo apt-get install -f
sudo apt-get autoclean
sudo dpkg --configure -a
```

---

### Post by joshwaaa on 2010-03-27
Agree with the above.
 
Further more you could kill the process that is using package manager.
 
$ ps -ef 
 
look for synaptic or whatever the package manager is called
 
then
 
$sudo kill -9 process-id
 
cheers,
 
Joshwaaa

---

### Post by 5349U11 on 2010-05-09
> **spiderbatdad said:**
> maybe this:
```
sudo apt-get install -f
sudo apt-get autoclean
sudo dpkg --configure -a
```

that helped me, thanx :)

---

