---
title: "Removal of Unity"
date: 2011-10-28
forum: General Help
---

### Post by chrisjoffe on 2011-10-28
Can Unity simply be removed without doing damage?  The software center threatened that Gnome3 the the Unbuntu Desktop System would no longer be updated if I did so.

---

### Post by LowSky on 2011-10-28
11.04 = no

11.10 = yes... i think

---

### Post by Ric_NYC on 2011-10-28
> **LowSky said:**
> 11.04 = no

**11.10 = yes... i think**



**Hallelujah!!!**

---

### Post by chrisjoffe on 2011-10-28
I would really love to be able to get that thing off my machine.  I was going to leave it be but every time my system updates, they set the default desktop back to Unity.  I'd really like them to just do they updates and leave the configuration alone.

---

### Post by cariboo on 2011-10-29
This is more a support question, than something you'd ask around the water cooler at work.

---

### Post by oldtimer7777 on 2011-10-29
> **chrisjoffe said:**
> I would really love to be able to get that thing off my machine.  I was going to leave it be but every time my system updates, they set the default desktop back to Unity.  I'd really like them to just do they updates and leave the configuration alone.

I wish we could have Gnome 2 back and be able to remove Unity completely..  I want 11.10 with Gnome 2..  but that isn't going to happen.

---

### Post by DoubleClicker on 2011-10-29
> **oldtimer7777 said:**
> I wish we could have Gnome 2 back and be able to remove Unity completely..  I want 11.10 with Gnome 2..  but that isn't going to happen.

Actually it is happening.  The Mate Desktop Environment is a fork of Gnome 2, that is being continued.    

see: [http://ubuntuforums.org/showthread.php?t=1858282](http://ubuntuforums.org/showthread.php?t=1858282) 

There should be a PPA available by Monday.

Also, I've removed Unity, and have not yet detected any problems from it.

---

### Post by chrisjoffe on 2011-10-29
I'm personally happy enough with Gnome3, now that I've got it customized a bit... I just want Unity gone.   Anybody know how to do this with a reasonable certainty of not doing permanent damage to the rest of my system?

---

### Post by philinux on 2011-10-29
> **chrisjoffe said:**
> I'm personally happy enough with Gnome3, now that I've got it customized a bit... I just want Unity gone.   Anybody know how to do this with a reasonable certainty of not doing permanent damage to the rest of my system?

Have you seen the sticky in here for classic gnome. Also the Lubuntu option see sticky in installation and upgrades. Endless options with DE's.

---

### Post by chrisjoffe on 2011-10-29
I don't actually want to go back to Gnome2/classic or reinstall a different distro.  I use Gnome3 in 11.10 just fine.  All I want is to remove Unity so it doesn't continually get reconfigured as my default desktop every time Canonical does an update.

---

### Post by knutschr on 2011-10-29
I was totally disapointed after uppgrading to 10.10
I Installed 11.04 and chose classic mode.
As good as Ubuntu is now, it didn't take long to make everything as it was :-)

---

### Post by aeronutt on 2011-10-29
> **chrisjoffe said:**
> I don't actually want to go back to Gnome2/classic or reinstall a different distro.  I use Gnome3 in 11.10 just fine.  All I want is to remove Unity so it doesn't continually get reconfigured as my default desktop every time Canonical does an update.

Hmmm...I'm using 11.10 and gnome-shell, with Unity still installed, and gnome-shell stays as my default after I update. Even so, I'd like to remove Unity. :)

---

### Post by Bobhuber on 2011-10-29
> **chrisjoffe said:**
> I don't actually want to go back to Gnome2/classic or reinstall a different distro.  I use Gnome3 in 11.10 just fine.  All I want is to remove Unity so it doesn't continually get reconfigured as my default desktop every time Canonical does an update.
Install Synaptic package manager
BACK UP YOUR SYSTEM FIRST
In 11.10 remove all files that START with the name unity EXCEPT the following
unity-services
unity-asset
unity-greeter
unity-common
sudo apt-get autoclean (this will clean the cache only)
reboot

---

### Post by chrisjoffe on 2011-10-29
I had read that info before.  The other authoritative answer was to just use the software center to do it but it gave dire warnings so I wanted to be hear from some who had done it or knew for sure.

---

### Post by Bobhuber on 2011-10-29
> **chrisjoffe said:**
> I had read that info before.  The other authoritative answer was to just use the software center to do it but it gave dire warnings so I wanted to be hear from some who had done it or knew for sure.
DO NOT USE THE SOFTWARE CENTER . You will be reinstalling from a backup or fresh install.
I'm running Gnome3 without Unity right now.

---

### Post by chrisjoffe on 2011-11-01
Well.... I followed your instructions to the letter.  Following the next update, the system appears to have tried to reset itself to Unity and failed because now I have no real shell at all.  It seems to have defaulted to an extremely primitive file-manager-only shell.

Any ideas how to recover from this?

---

### Post by chrisjoffe on 2011-11-01
Alright... I managed to force a logout and choose Gnome for my shell and it seems to work.  Any idea how to prevent this from happening the next time they feel like updating shell components?

---

### Post by cbowman57 on 2011-11-02
Have you tried removing the ubuntu-desktop package?

---

### Post by DapperMe17 on 2011-11-02
This is slightly off-base, but have you given Xubuntu (XFCE) a chance? Xubuntu & XFCE have made tremendous strides over the last two releases, and are absolutely outstanding in terms of visual looks and easy configuration.

---

### Post by chrisjoffe on 2011-11-02
I've actually gotten to like the look of GnomeShell, now that I've extended and themed it.  I just want the system to quit trying to jam me back onto Unity... especially since it isn't (mostly) installed anymore.

---

### Post by markbl on 2011-11-02
Force gnome-shell to be the default with the following command:
```

sudo /usr/lib/lightdm/lightdm-set-defaults --session gnome-shell

```

---

