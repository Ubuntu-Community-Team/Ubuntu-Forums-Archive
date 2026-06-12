---
title: "Trying to install Gloobus"
date: 2010-08-01
forum: General Help
---

### Post by FlyingIsFun1217 on 2010-08-01
Interested to see how it works, I attempted to install Gloobus from the Launchpad PPA. Upon adding it and going to install gloobus-preview, I am told that I first need to install libgvfscommon0. So I go ahead and attempt to do such, and am told that the following packages are to be removed:

> brasero deskbar-applet gdm gdm-guest-session gnome-about gnome-applets
  gnome-mag gnome-panel gnome-power-manager gnome-session gnome-utils gvfs
  gvfs-backends gvfs-bin gvfs-fuse indicator-applet indicator-applet-session
  indicator-me libbonoboui2-0 libgail-gnome-module libgnome-pilot2 libgnome2-0
  libgnome2-perl libgnome2.24-cil libgnomepanel2.24-cil libgnomeui-0
  liblpint-bonobo0 libpanel-applet2-0 mintmenu mousetweaks nautilus
  nautilus-image-converter nautilus-script-audio-convert
  nautilus-scripts-manager nautilus-share python-gnome2 python-gnome2-desktop
  python-gnomeapplet python-pyatspi rhythmbox rhythmbox-plugin-cdrecorder
  rhythmbox-plugins startupmanager system-config-printer-gnome ubuntu-tweak

Umm... definitely want to keep all of those. Is this normal? Why is the installation of one library attempting to wipe out half of my system? Is there a way to prevent this?

Thanks
FlyingIsFun1217

---

### Post by oaxacamatt1 on 2010-08-01
Hmmmm... 
Well, It does not seem 'normal' that it would ask you to delete all those files but the heck is normal anyway...  And actually I would not delete those.

I guess I would start at the basics level. What version of Ubuntu are you using?  Also how exactly did you try to install the prog? Because when I went to the gloobus site it mentioned loading an older version via luanchpad.  This might be helpful.

On another tact, It seems when I went to the Gloobus website there were different ways to install the prog.  Have you tried the .deb packages that are on the site or have you thought about going to source code and installing that way?  
Cheers,
M

---

### Post by FlyingIsFun1217 on 2010-08-01
Version is 10.04

All of the install methods you have suggested, I have indeed tried. Tried installing from source, needs libgvfscommon0. Tried installing from a downloaded .deb installer, needs libgvfscommon0. Added the PPA, tried installing that way, needs libgvfscommon0.

It seems to be a pretty strict requirement for the library, which is why I would consider the problem the fact that it wants me to remove all the other packages to install it.

Thanks

---

### Post by hansdown on 2010-08-01
Hi FlyingIsFun1217.

I tried installing the 64bit .deb.

I got a failure to install error.

Not much help, but it could save some strife.

---

### Post by FlyingIsFun1217 on 2010-08-01
Tried installing again from a .deb, and I have yet again been prompted to remove the other 45 packages before I can install Gloobus.

Still not entirely sure why I would have to remove all of these packages.

FlyingIsFun1217

---

### Post by oaxacamatt1 on 2010-08-03
It sounds Gloobus is not ready for 'Prime Time.'

I went to the Gloobus site and found a number of people with install problems.  They have not mentioned your particular problem though. It seems like a mixed bag.  Some can... Others can't...

[http://gloobus.wordpress.com/2010/05/05/covergloobus-ppa-problems/](http://gloobus.wordpress.com/2010/05/05/covergloobus-ppa-problems/)

[http://gloobus.wordpress.com/2010/05/04/covergloobus-for-lucid/](http://gloobus.wordpress.com/2010/05/04/covergloobus-for-lucid/)

HTH
M

---

### Post by FlyingIsFun1217 on 2010-08-04
Well, there do seem to be problems for those folks, but that's all pertaining to Cover Gloobus, which is actually a different program in a different PPA. I'm just trying to install the vanilla Gloobus.

I'm surprised one of those brainiacs doesn't know the cause of this. I'll keep searching around.

FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2010-08-07
Shameless self-bump. Nobody knows what's going on here?

---

### Post by Balthazar_Droid on 2010-08-08
Not a lot of help, but I am having the exact same problem. Hopefuly someone knows how to fix this.

---

### Post by FlyingIsFun1217 on 2010-08-16
Well, I've given up on this. It's not an essential package to have, and I don't feel like destroying my system just to attempt to install it.

FlyingIsFun1217

---

### Post by megamanexent on 2010-08-20
Well I need a work around, What about installing libgvfscommon0 from source, do you think that will work?

Its not essential,but I really would like to try it!

**UPDATE**

I got it installed!!

What I did was follow this wiki ([http://gloobus.net/wiki/index.php?title=Install#Installing_Gloobus_Preview_from_the_PPA](http://gloobus.net/wiki/index.php?title=Install#Installing_Gloobus_Preview_from_the_PPA)) and download the source for Gloobus-preview and coverglobus. In the source, there is a README file, open it and install the dependencies there. ./autogen.sh, make, sudo make install, and your done. Didn't of to un-install gdm and such for it!

Also elementary-nautilus has bindings for it already!

---

### Post by ammonkey on 2010-08-21
gloobus package has been updated, libgvfscommon0 dependency has been removed like it was an old deprecated dependency.

---

### Post by FlyingIsFun1217 on 2010-08-23
> **ammonkey said:**
> gloobus package has been updated, libgvfscommon0 dependency has been removed like it was an old deprecated dependency.

Perfect, it seems to be working for me now. Much appreciated.

FlyingIsFun1217

---

