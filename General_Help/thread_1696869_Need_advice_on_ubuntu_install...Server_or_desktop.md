---
title: "Need advice on ubuntu install...Server or desktop?"
date: 2011-02-28
forum: General Help
---

### Post by Sara_L on 2011-02-28
Hi. I'm trying to get an ubuntu system up and running, but i'm haveing trouble selecting the right flavor. Server dosent seem to have enough easy to use tools and desktop seems to have wayy to much.

The system in question is an old p-4 with 1G of ram, a 120G sata disk that dual boots XP

I need it to be a HTPC, a Samba server for files, and to be able to forward X11 clients (such as emulator with the inputs connected to the machine, a cd/dvd burning app,etc), and a VM host for an old IPX dos app to control my old dos machine. I'll be useing Cygwin on my XP laptop for the front end for everything. I also plan to run few services going out over the internet, which is why i prefer to start with a server build for security. (a streaming server like tversity and apache for b2evolution, a blog)

I need the X server to be minimual yet be able to use the properity nvidea driver to properly setup both outputs of the video card (TV-out for display of video from whatever media player is installed and the emulator)

I need recommendations as far as what flavor i should be starting out with and how i can go about setting it up.

Thanks

---

### Post by mastablasta on 2011-02-28
i am not sure exactly what you are trying to do with the computer, but let me tell you a little secret. both server and Ubuntu are the same. they just have different programmes installed and server donsn't have any GUI desktop but only CLI. 
 
you can always uninstall the applications you don't want or need. and you can do that quite fast. you can easilly install the ones you do need.
 
If you are experienced in linux you can use a minimal ISO and then build your own system from that. if oyu want to go even more hardcore into this then Linux From Scratch is for you. ;-)

---

### Post by seawolf167 on 2011-02-28
> **mastablasta said:**
> both server and Ubuntu are the same. they just have different programmes installed and server donsn't have any GUI desktop but only CLI. 
 
you can always uninstall the applications you don't want or need. and you can do that quite fast. you can easilly install the ones you do need.


Aye, if you install the server version you can always install a GUI (though there is a reason it doesn't come with one - because on a server you don't want a GUI taking up CPU cycles).

```
sudo apt-get install ubuntu-desktop
```

On the desktop version you can always uninstall things like Open Office which you wouldn't need

```
sudo apt-get purge openoffice*
```

---

