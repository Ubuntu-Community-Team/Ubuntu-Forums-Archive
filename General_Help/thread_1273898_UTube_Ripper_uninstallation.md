---
title: "UTube Ripper uninstallation"
date: 2009-09-23
forum: General Help
---

### Post by tom.swartz07 on 2009-09-23
Hi folks,

I have a bit of an IT problem. My brother installed UTube Ripper on his system earlier today, and after trying it out, decided that he doesnt like it. He followed the directions posted here: [http://www.ubuntugeek.com/downloadextract-audio-from-youtube-videos-using-utube-ripper-in-ubuntu.html#more-661](http://www.ubuntugeek.com/downloadextract-audio-from-youtube-videos-using-utube-ripper-in-ubuntu.html#more-661) He cannot figure out how to remove it, so he put me in charge to get rid of it.

Im about 50 miles away, but I am able to connect via ssh. 
Does anyone have a way to remove UTube Ripper easily through ssh?


Thanks for anything!
Tom

---

### Post by yabbadabbadont on 2009-09-23
Try "sudo apt-get --purge remove utube-ripper".  If it automatically pulled in some dependencies when it was installed, you might want to run "sudo apt-get --purge autoremove" to get rid of them too.

---

### Post by tom.swartz07 on 2009-09-23
Hi,

Thanks for the quick reply, but it appears that utube-ripper is not the name of the package...

Here is where Im thrown off the trail a little bit. I know that the program is still there, because the directories created by running the program are there, yet it doesnt want to respond to utube-ripper package command.

Does anyone know specifically what the name of the package is?

---

### Post by yabbadabbadont on 2009-09-23
That was the name according to the script I downloaded... maybe it has changed in the latest version?  Try finding it with either "aptitude search utube" or "apt-cache search utube".

---

### Post by tom.swartz07 on 2009-09-23
$ aptitude search utube
p   libwebservice-youtube-perl - Perl module that provides an interface to YouTube services                      
i   utube                    - Utube Ripper can download and convert your Youtube videos.                      
p   youtube-dl                                       - download videos from youtube.com 


From this, I would assume the name has changed to simply 'utube'?
Tried it, and it worked.

Thanks a ton Yabba!!

and now...
$ sudo shutdown -h now

---

### Post by saxophobe on 2010-08-28
I removed this using the sudo apt-get --purge remove utube command also!

This application doesn't work on 10.04.  Thanks for the info!

---

### Post by ericmc783 on 2010-12-18
just for the record I had the same problem.

I used ```
sudo apt-get remove utube
```

Worked for me.

---

### Post by Ziadance on 2011-03-02
> **ericmc783 said:**
> just for the record I had the same problem.

I used ```
sudo apt-get remove utube
```Worked for me.

Worked for me too.  Thanks guys.

---

