---
title: "enable gnome-shell on ubuntu 11.10"
date: 2011-10-14
forum: General Help
---

### Post by mjsilverstri on 2011-10-14
Hi,

I am running ubuntu 11.10 on virtual box 4.1.4 on Windows 7.
I did 'sudo apt-get install gnome-shell' to install gnome shell on ubuntu 11.10. 

But after I log in using 'gnome shell', I only get the gnome classic environment. I don't see the new gnome shell environment.

In my virtual box, I have already 'enabled 3d acceleration' and pu 128 MB ram. 

Any idea how i can get this to work?

---

### Post by volkerbradley on 2011-10-14
Forgive me if this reply is not helpful.
When I get to the login screen, there is a spoked wheel to the right of my name. When I click on Gnome 3 and then log in, I am in the Gnome Shell.  Is this different from what you are seeing?

---

### Post by hsoulen on 2011-10-14
> **mjsilverstri said:**
> Hi,

I am running ubuntu 11.10 on virtual box 4.1.4 on Windows 7.
I did 'sudo apt-get install gnome-shell' to install gnome shell on ubuntu 11.10. 

But after I log in using 'gnome shell', I only get the gnome classic environment. I don't see the new gnome shell environment.

In my virtual box, I have already 'enabled 3d acceleration' and pu 128 MB ram. 

Any idea how i can get this to work?

There are a few suggested ways to get this to work in VB, the below is for running a Fedora 15 Guest but the instructions should be about the same for Ubuntu:

[http://www.sysprobs.com/get-working-fedora-15-gnome-3-shell-in-virtualbox]("http://www.sysprobs.com/get-working-fedora-15-gnome-3-shell-in-virtualbox")

One note... I have NEVER been successful with running either Gnome 3 or Unity 3D in VirtualBox, but your mileage may vary.

Cheers,

Hank

---

### Post by mjsilverstri on 2011-10-14
> **volkerbradley said:**
> Forgive me if this reply is not helpful.
When I get to the login screen, there is a spoked wheel to the right of my name. When I click on Gnome 3 and then log in, I am in the Gnome Shell.  Is this different from what you are seeing?

I only see 'Gnome' 'Gnome Classic' 'Gnome Classic (no effect)'
I don't see 'gnome 3'.

I see the same screenshot (the 2nd screen shot) as in
[http://www.ubuntugeek.com/how-to-install-gnome-shell-in-ubuntu-11-10-oneiric-ocelot.html](http://www.ubuntugeek.com/how-to-install-gnome-shell-in-ubuntu-11-10-oneiric-ocelot.html)

But i don't think that is gnome3 shell.

---

### Post by mcduck on 2011-10-14
That is the fallback mode of Gnome Shell, used in case you don't have graphics card & drivers that are capable of running accelerated graphics.

Anyway, since you are running Ubuntu in Virtualbox, you'll have to install the *virtualbox guest additions* package to get things like graphics acceleration working. After you've done that you should be able to run the normal Gnome Shell session, assuming your graphics card & drivers are up to the task.

---

### Post by Ethr on 2011-10-21
I'm having this issue too. Just doing:

```
sudo apt-get install virtualbox-guest-additions
```

as we speak

I installed the iso which came with VB but had no success.


No success.

Any ideas?

Annoyingly I got the gnome3 (full) shell to work when i installed it from 11.04's PPA. I upgraded and it stopped :(.

---

### Post by plasmafusion on 2011-10-21
haven't tried it in a vm but it worked fine with 11.10 beta and the final release on my main machine.
gone over to lxde though as i find unity and gnome 3 make me less productive.

---

### Post by Ethr on 2011-10-21
Gnome 3 has a big learning curve but once you remember a couple of shortcuts (or alter them of course) then its really really good.

Being a vim addict I dont like using the mouse if I can help it. Gnome 3 and Unity are more key-board centric which makes my life alot quicker. Also they seem to have found a nicer balance between 'touch screen' features and 'mouse features'.

Its a shame gnome3 doesn't have a 2D fall back like Unity does as I prefer to use it.

---

### Post by Schr on 2011-10-28
I'm running gnome shell in 3d mode under virtualbox. I don't think i did anything special to get it working

Here is what I did (if i remember it all)

1. VirtualBox quest additions are installed from the ISO provided by VirtualBox (ie no ubuntu packages). Host OS is Windows 7
2. I think i had to reinstall the quest additions once due to a kernel upgrade
3. apt-get install gnome-shell
4. Enabled 3d accelleration with 128MB RAM
5. Reboot

Only thing is that for some the full screen resolution for the virtual machine is 1664x940, where as in the host OS it actually is: 1650x1050. Without 3D acceleration and the fall back to non-gnome shell I could get the full host os resolution.

---

### Post by mcasperson on 2011-12-29
[This is a screencast]("http://www.squidoo.com/enable-the-gnome-shell-in-fedora-16-and-virtual-box") that details the process for running the Gnome Shell in Fedora 16 under VirtualBox. I would assume that the process is much the same for Ubuntu.

---

