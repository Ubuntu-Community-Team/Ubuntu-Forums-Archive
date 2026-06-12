---
title: "Bash Script"
date: 2009-12-04
forum: General Help
---

### Post by lewisforlife on 2009-12-04
I want to run a bash script when a certain user logs in.  I know I can use update-rc.d to run a script for all users, but I only want to run the script for a certain user.  Is this what .bashrc is?  Would .bashrc be the proper place to run custom scripts during login?

---

### Post by fluffman86 on 2009-12-04
Only if they are opening a terminal of some sort (gnome-terminal or a TTY).  If they are logging in via GDM, you should add a script to System > Preferences > Startup Applications

---

### Post by Sam on 2009-12-04
Use System > Preferences > Startup Applications and add your script here.

---

### Post by lewisforlife on 2009-12-04
It will be run from xterm, with X Server running.  No desktop environment will be running though.

---

### Post by Johnny B on 2009-12-04
> **lewisforlife said:**
> It will be run from xterm, with X Server running.  No desktop environment will be running though.

you sound confused.

---

### Post by falconindy on 2009-12-04
> **Johnny B said:**
> you sound confused.
err, I think you're more confused. Running Xterm on an Xserver with nothing else is entirely possible.

Add your startup applications to ~/.bash_profile

---

### Post by lewisforlife on 2009-12-05
This worked great, thanks falconindy.  I am running xterm on xserver without a desktop environment, the reason is because I am wanting to load a GTK+ POS system that I am working on so the user can process transactions without having the rest of desktop stuff.

---

