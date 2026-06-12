---
title: "Cannot log in to gdm"
date: 2009-11-04
forum: General Help
---

### Post by pythonscript on 2009-11-04
I installed a command line only ubuntu from the alternate install CD, then installed the *lubuntu-desktop* package that's new in the karmic repos. For some reason, however, I can't log in to gdm... I can log in using a virtual terminal, but if I'm on tty7 (the x server) I type my password under my username, click Log In, and it brings me right back to the log in screen.

I know I'm using the right password, since this is only a test machine, so both the username and password are the letter "u" Hard to mess up, eh? Any ideas how I can make this work? I'm really excited about Lubuntu 10.04 in April, so I wanted to test out the metapackage as soon as I could. Thanks!

---

### Post by Giblet5 on 2009-11-04
Does user "u" own /home/u and /home/u/*?

Does user "u" have a ~/.xsession-errors file?

---

### Post by robopoboy on 2009-11-04
from a console

sudo apt-get install gdm

sudo apt-get -f install

reboot

from a console

this will make sure you have all of gdm

sudo apt-get install gnome

sudo apt-get -f install

reboot

ithat will assure all your required files are in place?

There may be a policy in place for minimum password length or complexity?

---

### Post by pythonscript on 2009-11-04
> **Giblet5 said:**
> Does user "u" own /home/u and /home/u/*?

Does user "u" have a ~/.xsession-errors file?

I'll give this a shot once I'm back in my flat; I didn't even think of this, but that would explain it...

> **robopoboy said:**
> 
sudo apt-get install gnome
sudo apt-get -f install
reboot

that will assure all your required files are in place?
There may be a policy in place for minimum password length or complexity?

Installing gnome would defeat *the entire purpose* of installing a command line only system and the lubuntu-desktop package. gdm installs as part of this metapackage, hence why it's installed, but I'm not going to install all of gnome just for the log in manager to work. If it seriously comes down to a problem with gdm, I'll remove it completely and just use slim. 

No, ubuntu doesn't have a policy about minimum password length/complexity. It'll warn you during the install about using a weak password, but this is my "standard" for my ubuntu test machines, and the 30 or so machines I've used this identical combination on (some of which are ubuntu 9.1, albeit with different desktop environments) never complained or refused to log in because of it.

---

### Post by pythonscript on 2009-11-04
All right, I ran:
```
sudo chown u /home/u
```

and an .xsession-errors file does exist in the directory, and when I cat inside it, it lists an error of:

```
WARNING **: Unknown option --choose-session=openbox-session
```

Any idea what this means? Also, according to ls -al, u owns everything in its home directory (except for .. but  I figured that). Any ideas? Thanks!

---

### Post by Giblet5 on 2009-11-05
I don't recognize that error. I'm also unfamiliar with lubuntu.

What *might* work is to explicitly select a lubuntu session from the gdm login screen.

(I *think* the new gdm still lets one select session type - I was disgusted by the absence of a remote session option, xdmcp, and switched to kdm)

Living on the bleeding edge is bloody...

---

### Post by pythonscript on 2009-11-05
How embarrassing... I simply forgot to select LXDE as the session; this is working perfectly now, and I must say, the ultra-low memory consumption puts XFCE to shame. I'm quite excited for Lubuntu 10.04 in the future.

---

### Post by Giblet5 on 2009-11-05
> **pythonscript said:**
> How embarrassing... I simply forgot to select LXDE as the session; this is working perfectly now, and I must say, the ultra-low memory consumption puts XFCE to shame. I'm quite excited for Lubuntu 10.04 in the future.

I'm amazed it was that!

Excellent. (Installing now......)

Don't forget to mark this thread SOLVED via the Thread Tools dropdown.

Cheers!

---

