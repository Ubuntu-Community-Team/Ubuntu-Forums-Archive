---
title: "Rolling my own Ubuntu .iso?"
date: 2011-04-26
forum: General Help
---

### Post by FrankTheTankC on 2011-04-26
During spring break, I decided to roll my own Ubuntu-based distro.
I accomplished this using the ubuntu-minimal disk, and a dirty post install script, which handles installing X and other programs, copying over config files, and editing files that contain Ubuntu branding (don't worry, I didn't remove it all, I made it so the text-boot says "Current Base: Ubuntu 10.10")

the emphasis on my roll is to allow for easy connectivity between my systems using synergy, VNC, nmap (to find other computers on the network), dropbox, and the easy file managing GUI from nautilus, while keeping it light, using fluxbox for the WM, and eschewing GDM in favor for a text-based login.

anyway, after finals, I'd like to refine it. I really want to put it together onto a burnable ISO so I could distribute it to friends and not rely on an internet connection to install it.

How can I go about doing this?

---

### Post by earthpigg on 2011-04-26
hi,

yup.

[remastersys]("http://geekconnection.org/remastersys/").

---

### Post by FrankTheTankC on 2011-04-26
SCORE.
Thanks, I hope this works!
I'll be trying it after the 5th.

---

### Post by earthpigg on 2011-04-26
it [worked for me]("http://sites.google.com/site/masonux/home/notes-to-myself"). :P

---

