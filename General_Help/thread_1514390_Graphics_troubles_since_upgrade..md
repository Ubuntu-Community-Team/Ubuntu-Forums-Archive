---
title: "Graphics troubles since upgrade."
date: 2010-06-20
forum: General Help
---

### Post by yoshimitsuspeed on 2010-06-20
So I upgraded from Kubuntu 9.01 to 10.04 and I started getting compositing suspended errors. 
I started this thread and it really hasn't gotten me anywhere. 
[http://ubuntuforums.org/showthread.php?t=1470642](http://ubuntuforums.org/showthread.php?t=1470642)

After playing around more and more I think that is a symptom of a bigger problem and I'm pretty sure it's related to my graphics driver or Kubuntus relationship with it. 

I have a Nvidia GTX 9800 

With Nvidia current installed the computer functions pretty normally other than the suspended compositing. 
However on startup the resolution is horrible, everything is huge and when the splash screen finally pops up it looks all wrong. The kubuntu takes up most the screen and the colors are messed up. 
Once the login manager pops up everything looks normal.
Now here's where it gets weird. If I uninstall nvidia-current, on startup my resolution is normal. It never goes to the splash screen and takes me straight to terminal mode which still has good resolution. 
After I do whatever I do there and restart I finally see what the splash screen should look like while it's logging out. The Kubuntu is small and there is shading and everything looks right. 
So now if I go into terminal I can install nvidia current and run nvidia-xconfig and it's back to how it started.

I downloaded Nvidias beta from their site but if I uninstall Nvidia-current and try to install the beta it says I cannot because there is another driver in the way (Forget the names it sugests but they are odd and I haven't heard of them before) or it is the wrong driver for my computer. 
I searched synaptic (Yeah I use synaptic in KDE) for the drivers and nothing came up. I am pretty confidant it is the right driver for my computer.

Once I accidentally installed the beta without removing the current and it functioned normally untill I tried removing current. Then it wouldn't work just like with no driver. I finally got the beta uninstalled and current reinstalled and here I am back at ground zero. 

Oh also I cannot startup in safe graphics mode. I have tried from the login window and also if I select recover mode in grub. I also tried with graphics drivers installed and without. Nothing.

---

### Post by yoshimitsuspeed on 2010-06-21
OMG made it to page ten in as many hours. 
I was wondering why I have gotten so little help on this. 
What's the deal too many people asking questions not enough answering or what?
I saw a lot of threads on the way to mine with zero posts too.

---

### Post by yoshimitsuspeed on 2010-06-21
Ok I found a bug report that explains the splash screen but none of my other problems. 
I am starting to wonder though if it's an issue that's been glazed over in the rush to jump to nouveau or whatever it's called.

I still can't use my computer without Nvidia current installed. I still keep getting the occasional suspended compositing. Oh and Google earth falls on it's *** too. A little reasearch told me it's probably graphics card or driver related too.

---

### Post by yoshimitsuspeed on 2010-06-23
Update. VLC sometimes works great. Sometimes it freezes up and won't play. Almost locks up the whole computer and takes a minute to close. 

Kinda depressed about how little input I have gotten. 
I seem to remember this forum being different.

---

### Post by yoshimitsuspeed on 2010-07-03
Ok I think I have found a solution.

As far as I can tell this is a problem between Nouveau and the proprietary Nvidia driver. I'm a little pissed they implemented this Nouveau thing so far before it was ready. 
Anyway uninstalling Neauveau is not enough. 
I had to blacklist it as explained in this thread.
[http://ubuntuforums.org/showthread.php?t=1519849&highlight=nouveau](http://ubuntuforums.org/showthread.php?t=1519849&highlight=nouveau)
Before that I was getting the same fault he did when trying to install a Nvidia driver direct from Nvidia.
The repo version installed but caused all these problems.
Once I did
```
sudo apt-get --purge remove xserver-xorg-video-nouveau
```

Then

> **HomeSlixe said:**
> try this in terminal  ```
sudo nano /etc/modprobe.d/blacklist.conftv 
``` Add these:


blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

Then...

ctrl O to write
crtl X to quit

[CODE]sudo apt-get --purge remove nvidia-*


Then deleted my xorg.conf 
I restarted and entered console and installed Nvidias current version I had downloaded. Nvidia currently has a newer version than the repos.

Nvidia-current might work as well after blacklisting Neauveau, I'm not sure since I didn't try it.

However after doing all that and installing Nvidias 256.35 driver I haven't had a problem. 
Compositing has been fine, VLC, etc, even google earth works now. 
Pretty much all the graphics troubles I was having are gone. 

I'll update if anything funky shows up.

---

### Post by yoshimitsuspeed on 2010-07-07
Update

I have had VLC crash the system a couple times. 
Compositing becomes disabled and VLC freezes up hard. 
I started using Dragon player and haven't had a problem since.
I could attribute VLC freezing up to something separate but the way it disables compositing when it happens is too coincidental. 
That said if that's the only place it pops up I can live with it.

---

