---
title: "Dapper Drake..."
date: 2006-03-30
forum: General Help
---

### Post by frizzl on 2006-03-30
Hey guys, 

Just recently got into Linux... as in yesterday :P
and now Dapper Drake has come out. 

With my Ubuntu installation, will I be able to install Dapper Drake and retain all my users, files, setup etc? 

Also, will I be able to do this with a bootdisk? (Eg, Install disk)

Thanks guys :)

---

### Post by krusbjorn on 2006-03-30
Dapper is still in development and wont be released until the biginning of june. If you are new to linux, you really should stay with breezy. 

But to answer your question: Yeah, you could upgrade to dapper. Either by doing an installation from scratch by downloading the dapper flight CD and then install it by wiping your current system. OR you could change all the "breezy" to "dapper" in your /etc/apt/sources.list file. 

But as i said, you probably should stick with breezy until dapper is finally released.

---

### Post by frizzl on 2006-03-30
yes, i will be staying with breezy, but june isnt that far away, and i like to plan ahead :D

so... will i be able to install over breezy with the dapper disk? (when its out)

---

### Post by krusbjorn on 2006-03-30
Oh i forgot to mention: in the latter method, your users, files, setup etc will be kept. I always do a clean install when when installing a new release. Mostly to clean up the mess i have made, but also to repeat everything that needs to be set up, to keep my knowledge up to date (and to learn new stuff) :)

---

### Post by PhoenixP3K on 2006-03-30
Well Dapper is not out, unless I didn't wake up this morning and we're June 1st already.

But if you've installed Ubuntu 5.10 Breezy Badger right now you will be able to upgrade to the next version.

---

### Post by krusbjorn on 2006-03-30
(Sorry for making new posts instead of editing, but the edit function doesnt work here. Strange :confused: )

If you install with the CD, you will wipe your system. If you upgrade by changing your sources.list and doing "aptget -update" and "apt-get dist-upgrade", you will "install over breezy".

---

### Post by spartan777 on 2006-03-30
actually dapper isn't out yet. what you've heard of is dapper flight, a more human term for the beta. so, its the beta that's out now. dapper officially doesn't come until june 1st, since it was delayed 6 weeks. I'm not 100% sure, but I think you can just upgrade to dapper from your breezy badger install, everything intact.

---

### Post by frizzl on 2006-03-30
hmm, and will dapper be released with shipit as is breezy?

thanks people :D

---

### Post by krusbjorn on 2006-03-30
[QUOTE=frizzl]hmm, and will dapper be released with shipit as is breezy?[/QUOTE]

Of course :D (actually, i dont know, but i cannot in my wildest imagination believe that it wont)

---

### Post by LanceM on 2006-03-30
I ran the update with apt on my test box. Everything went well and all the changes tha I had made after the breezy install were kept. The only problem I have is that my video card is not recognized and my system is now running at a resolution of 640x480 which is pretty obnoxious. I havn't had time to get the video set up correctly, I am planning on doing that tomorrow.

---

### Post by ranf on 2006-03-31
Just wanted to mention it. There is an upgrade tool being worked on:
[https://wiki.ubuntu.com/AutomaticUpgrade](https://wiki.ubuntu.com/AutomaticUpgrade)

---

### Post by LanceM on 2006-03-31
My screen resolution problem was self-inflicted. I use a switchbox and was not on the right port when the Ubuntu box restarted so it could not detect the monitor. One quick reboot and my problem was fixed.

---

### Post by Cursor on 2006-03-31
I did the update yesterday.  There were some 1400 packages to update, which took all night.  When it was done, the only thing broken was my NVIDIA drivers.  To be expected I guess, it's a new kernel.

---

