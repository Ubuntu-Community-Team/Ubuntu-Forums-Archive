---
title: "Trying to install xubuntu-desktop - some errors?"
date: 2010-04-21
forum: General Help
---

### Post by HHx66 on 2010-04-21
I've been trying to install the xubuntu-desktop package as I'd like to have both KDE and XFCE on my system, however anytime I try to install it I get this:

```
sudo apt-get install xubuntu-desktop                             
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xubuntu-desktop: Depends: gtk2-engines-pixbuf but it is not going to be installed
                   Depends: update-manager but it is not going to be installed
                   Recommends: jockey-gtk but it is not going to be installed
                   Recommends: update-notifier but it is not going to be installed
E: Broken packages

```

I've tried to fix broken packages via apt-get, but nothing, I tried installing the missing dependant packages, but then I just get: 
```
sudo apt-get install gtk2-engines-pixbuf
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gtk2-engines-pixbuf: Depends: libgtk2.0-0 (= 2.18.3-1) but 2.18.3-1ubuntu2.2 is to be installed
E: Broken packages
hellhammer@Colossus:~$ sudo apt-get install libgtk2.0-0
Reading package lists... Done
Building dependency tree
Reading state information... Done
libgtk2.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 80 not upgraded.

```

any help on this? I'm running Kubuntu 9.10 Karmic x86-64.

---

### Post by ankspo71 on 2010-04-21
To me it looks like they updated some packages in the repositories that require newer, but currently unavailable, packages as dependencies. It might take up to a few days for the developers to get the rest of those newer packages built. They have been working extra hard lately because of the next release of Ubuntu is just around the corner.

This is not the same as installing xubuntu-desktop, but...
Have you tried installing the base xfce desktop package called "xfce4"? Installing that will install the base xfce desktop, without all of the extra packages used by Xubuntu (eg, gnome-dependencies, xubuntu artwork, etc). This way you wouldn't have more than one text editor, update manager, cd burner, audio player, etc (because thay are all required by Kubuntu and Xubuntu).

---

### Post by bobcollard on 2010-04-21
Medibuntu has been down for a few days, you may not have access to all the sources you need.

---

### Post by HHx66 on 2010-04-21
Ah, alright, thanks. I'll try just installing the xfce desktop and then try anything else a few days later, although now that you mention it just installing xfce4 is probably for the best.

Thanks for the help.

---

