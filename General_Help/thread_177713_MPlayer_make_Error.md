---
title: "MPlayer make Error"
date: 2006-05-16
forum: General Help
---

### Post by mesh2005 on 2006-05-16
I have installed Ubuntu 5.10, I found a post on how to install mplayer at the following link: [http://ubuntuforums.org/showthread.php?t=31061](http://ubuntuforums.org/showthread.php?t=31061)
but I got an error with make:
make[1]: *** [libpostproc/postprocess.o] Error 1
make[1]: Leaving directory `/home/amir/MPlayer-1.0pre7try2/libavcodec'
make: *** [libavcodec/libavcodec.a] Error 2
Please tell me how can I fix it.

Thanks.:-k

---

### Post by Sef on 2006-05-16
Why are you compiling mplayer instead of using synaptic?

Systems > Administration > Synaptic Package Manager

---

### Post by Sutekh on 2006-05-16
That guide you are following is for an older release of Ubuntu (5.04). Since you are running 5.10 you can get mplayer in a much easier way.

Do you know how to add repositories?  If so you need to enable the **multiverse** repository.  

If you don't know how to add the multiverse repository, here's how.

First you need to backup and edit the file that contains the repository sources.
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list
sudo gedit /etc/apt/sources.list
``` When the text editor opens you need to uncomment (remove the # sign) these lines
```
# deb http://archive.ubuntu.com/ubuntu breezy universe
# deb-src http://archive.ubuntu.com/ubuntu breezy universe

...

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe
``` and add **multiverse** to the end of them.

They should look like this
```
deb http://archive.ubuntu.com/ubuntu breezy universe **multiverse**
deb-src http://archive.ubuntu.com/ubuntu breezy universe **multiverse**
 
...

deb http://security.ubuntu.com/ubuntu breezy-security universe **multiverse**
deb-src http://security.ubuntu.com/ubuntu breezy-security universe **multiverse**
``` Save the file and then refresh the repositories list and then install mplayer using these commands
```
sudo apt-get update
sudo apt-get install mplayer
``` 
Or open Synaptic (System -> Administration) and click Reload, and then Search for mplayer, mark it for installation and click Apply.

---

### Post by mesh2005 on 2006-05-17
will that include win32 and Quicktime codecs?
thanks

---

### Post by Sutekh on 2006-05-17
I imagine it does.

---

### Post by mesh2005 on 2006-05-17
it worked :) thanks a lot :)

---

### Post by Sutekh on 2006-05-17
Great stuff, no problem!

---

