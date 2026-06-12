---
title: "Auto-mounting partition issue"
date: 2010-04-30
forum: General Help
---

### Post by _0R10N on 2010-04-30
Hi everyone, I upgraded my system to Lucid (previously Karmic), and I'm loving it!!!. But here's a problem I got:

I have an ext3 partition where my music, and other files, are stored. This partition is set to no auto-mount at startup, in matter of fact, there's no line for it in the /etc/fstab file at all. Now, everything worked like a charm on Karmic (mounting the partition on /media/ each time I requested it), but on Lucid, I have a kind of odd behavior. When the system starts, there's already a directory named after the partition. I check for its permission and it's set only for root access. If I (as root) cd into it, there's nothing in it. OK, now if I proceed to mount the partition the same way I used to do in karmic, everything works fine but, of course, there's an underscore attached to the end of the directory name. This messes with some programs settings, like Rythmbox...

I would like to know where is this directory coming from, and if I might be able to get rid of it.

Thanks in advance!

Kind regards!

---

### Post by RolandFlagg on 2010-04-30
why not just delete that directory before mounting your actual directory? I think I had the same problem, and deleting solved it.
Make sure it really does not contain anything, and then delete it, use "sudo rm -rf" if necessary

---

### Post by _0R10N on 2010-04-30
Yeah, I think I'm gonna try that. Instead of removing the directory, I'm going to rename it, just in case. I still wonder what causes this, what for was that folder intended to?.

Kind regards!

---

### Post by _0R10N on 2010-04-30
renaming the folder solved the problem. Marking the thread as solved!..

Kind regards!

---

### Post by dino99 on 2010-04-30
MountManager will help you to tweak as you need, install it if not yet

---

