---
title: "Installing packages with no cd"
date: 2006-04-03
forum: General Help
---

### Post by inkieminstrel on 2006-04-03
I keep running into situations where I'm trying to install a package and it asks me to insert my Ubuntu CD.  Is there a way to get around this and download the required files from thet net?  

I do most of my admin on this machine from ssh, and I'd like to eventually pull the CD drive off of it.

---

### Post by pacman^ on 2006-04-03
Please. Use the Search option. I found this on 3 minutes search: 

[http://www.ubuntuforums.org/showthread.php?t=154456](http://www.ubuntuforums.org/showthread.php?t=154456)

---

### Post by tkiesel on 2006-04-03
The referenced thread is a little light on the info...

It's correct that you need to enter the following into the terminal:

```
sudo gedit /etc/apt/sources.list
```

Then in Gedit you want to comment out the line that refers to the CD-ROM drive. I think that it's usually the first line in the default sources.list, but I could be wrong about that.

Comment the line out by putting a # at the beginning of it.

From then on, you'll grab all of your apt-get and Synaptic updates off of the web.

Cheers,
-T

---

