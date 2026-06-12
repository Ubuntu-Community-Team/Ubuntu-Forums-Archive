---
title: "Cannot access ubuntu - GNOME hasn't been installed correctly"
date: 2011-06-06
forum: General Help
---

### Post by lifestreammm on 2011-06-06
I cannot access ubuntu anymore.

I have ubuntu 10.04LTS Lucid Lynx. 

Ubuntu always prompts me to do updates. On the last update, the system wasn't able to find 4 files online. So it aborted the update and reverted to the previous state. On the next startup I could still access ubuntu. But the startup after that I got the inlog-screen (with username and password), and even with the correct username and password that's as far as it goes. In the lower right corner it says:

Install problem!
The configuration defaults for GNOME Power 
Manager have not been installed correctly
Please contact your administrator.


What can I do to access ubuntu again? 

I can, when I reboot, start up in recovery mode (but I have no clue what to do with the prompt). I can also start up older 'kernels': kernel 2.6.32-30-generic, 2.6.32-29-generic, 2.6.32-28-generic, 2.6.32-24-generic. Each of them also has a recovery mode. Not sure if this is useful at all though.

Laptop: AMD Turion(tm) 64 Mobile Technology MT-37, 1.99 GHz, 1,00 GB RAM.
I have a windows partition, through which I put this on the forum.

Thanks for guiding me towards the path of light :)

---

### Post by nothingspecial on 2011-06-06
Log into the recovery mode with networking

Make sure you have a wired internet connection.

Type ```
 sudo apt-get install -f
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by lifestreammm on 2011-06-06
Thanks Nothingspecial,

I did it. I still get the same message:

Install problem!
The configuration defaults for GNOME Power 
Manager have not been installed correctly
Please contact your administrator.

What I did notice during the install, is that it said a lot 'No space left on the device'. The last time I accessed ubuntu I filled the hard disk to the brim, as a temporary measure because i didn't have my external hard disk with me.
But not sure if 'No space left on the device' is what causes it to still not work.

When I start ubuntu, at one point it gives a message 'Unknown controller version. You may experience problems.' Maybe helpful?

Can you help me get down to the core of this?

Thanks

---

### Post by nothingspecial on 2011-06-06
The fact there is no space left is probably the root of the problem

From the recovery mode

```
sudo rm /var/cache/apt/archives/*.deb
sudo apt-get auto remove 
```

See if that gives you enough space to run the previous commands.

---

### Post by lifestreammm on 2011-06-06
I did the first command sudo rm /var/cache/apt/archives/*.deb
and the answer was 'no such file or directory'

I did the next command sudo apt-get autoremove nevertheless, and it said '87.7 mb disk space will be freed'. So I definitely agreed with that, and that enabled me to access ubuntu again, and now I'm writing from ubuntu.

So, is the idea now that I run these commands?
 sudo apt-get install -f
sudo apt-get update
sudo apt-get dist-upgradeEverything seems to be working fine now...but I still need to do these?

Thank you

---

### Post by nothingspecial on 2011-06-06
The first error just means there was nothing to remove in there.

As for the other commands, they won't do any harm, they just fix any broken packages then update your system.

I'd definitely give yourself some more space though.

---

### Post by lifestreammm on 2011-06-06
Thanks nothingspecial

The idea is definietely to free up a lot more space.

I'll mark this thread as solved.

Cheers!
Life

---

