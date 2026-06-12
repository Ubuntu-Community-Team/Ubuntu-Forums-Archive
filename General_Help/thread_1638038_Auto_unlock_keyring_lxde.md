---
title: "Auto unlock keyring lxde"
date: 2010-12-05
forum: General Help
---

### Post by James- on 2010-12-05
I've installed lxde from the ubuntu server edition(for less bloat on my netbook)

I installed the lxde metapackage that is in the repository and installed network-manager

In the ~/.config/lxsession/LXDE/autologin
I put 
> 
@nm-applet

the problem I now face is that the gnome-keyring is always prompting for a password to unlock the keyring(which I do not want)

I've been trying to find the package that installs the gnome keyring manager to see if I can't tell it to autologin(one of the downsides to installing from scratch is finding the useful apps)

Any advice would be appreciated

---

### Post by cipherboy_loc on 2010-12-05
From my ~/.fluxbox/startup file, this is used to start nm-applet and the printing service while getting rid of the auto-login:

> 
nm-applet &
system-config-printer-applet &
gnome-keyring-daemon --start --components=pkcs11 &
gnome-keyring-daemon --start --components=secrets &
gnome-keyring-daemon --start --components=ssh &

gnome-settings-daemon &


it loads nm-applet, the printing service, gnome-settings, and the gnome-keyring-daemon. Type each command into the terminal to find any missing pieces that you may need. When I created my fluxbox startup, I pulled many things from my gnome startup. It never has prompted me for a password for my Wi-Fi.


Cipherboy.

---

### Post by James- on 2010-12-05
hmm weird still prompts me for password :/

---

### Post by James- on 2010-12-05
Well I found that it was a pam.d problem
I had to modify the following files
/etc/pam.d/xscreensaver   (added fallowing line)
> 
auth    optional        pam_gnome_keyring.so

and 

/etc/pam.d/passwd
> 
password        optional        pam_gnome_keyring.so


Then when it prompted me for the password I could check the "unlock automatically next time I login" check box in the details and it works perfectly without trying to start keyrings

---

