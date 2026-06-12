---
title: "How to install Remastersys in Ubuntu 10.10"
date: 2010-12-01
forum: General Help
---

### Post by rmcellig on 2010-12-01
How can I properly install Remastersys in Ubuntu 10.10?

---

### Post by sgosnell on 2010-12-01
Download the .deb file and install it with gdebi.

---

### Post by rmcellig on 2010-12-01
I can't find the deb file for 10.10.

---

### Post by sgosnell on 2010-12-01
It's not in the repositories, AFAIK, you have to get it from sourceforge.

---

### Post by Liverbones on 2010-12-01
> **sgosnell said:**
> It's not in the repositories, AFAIK, you have to get it from sourceforge.

Or follow the instructions on the Remastersys Backup website. Ubuntu 10.10 uses grub2, and using the version of Remastersys for Karmic seems to function perfectly fine in Maverick (for me, at least).

Just add this to your /etc/apt/sources.list:

[FONT="Monospace"]# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/[/FONT]

Then type [FONT="Monospace"]sudo apt-get update && sudo apt-get install remastersys[/FONT]. Voila. Note that when installing, Ubuntu will let you know that the remastersys package cannot be authenticated. I'm not sure if there is a public key for the repository, to be perfectly honest.

---

