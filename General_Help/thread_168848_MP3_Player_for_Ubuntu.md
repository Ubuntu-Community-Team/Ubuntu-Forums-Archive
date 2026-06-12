---
title: "MP3 Player for Ubuntu"
date: 2006-05-01
forum: General Help
---

### Post by revstar5 on 2006-05-01
Hi!
I've just installed ubuntu on my computer. It seems like a nice OS but lacks support to play formats like MP3, MPEG, etc. out of the box.

Also, my USB Router is not working under Linux.

So, Please tell me the names of some apps that I can use to play MP3s that come with binaries for Ubuntu/Debian (And that are easy to install!!!)

PS: Please no Synaptic, no apt-get!!!!!!!!!!!

---

### Post by Ramses de Norre on 2006-05-01
Try [this]("https://wiki.ubuntu.com/RestrictedFormats"). And why don't you want to use apt or synaptic?? It's the only way to avoid dependency hells and they make it very easy to monitor and remove installed apps.

---

### Post by derjames on 2006-05-01
Hi there
MP3 is a restricted format under LINUX, please read the following wiki for more information about the topic... good luck

[https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29)

cheers

---

### Post by Jagot on 2006-05-01
I'm afraid to tell you that Syanptic is the easiest way to install things in Ubuntu, and you will have to use it at some point, along with apt-get.  This is not like Windows - no double-clicking to install software, but it really isn't very difficult.  Here's a nice guide to installing software:

[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

Ubuntu already comes with an MP3 capable player in rhythmbox, however you will need to install some packages to enable you to play MP3 files.  You will need to follow this guide to do so:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by revstar5 on 2006-05-01
I can't use synaptic or apt-get bcoz my modem /USB router is not supported under linux ie. no internet connection!!!!!!!!!

---

### Post by Ramses de Norre on 2006-05-01
You'll need it for any package you want to install that's not on the cd-rom.. and non-open source stuff like mp3 support will never be on install cd's.. 

Or you can look for the needed packages [here]("http://packages.ubuntu.com/breezy/") and download them with there dependencies, then in ubuntu install the packages with sudo dpkg -i /path/to/package.deb.
Install the dependencies first!

---

