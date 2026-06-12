---
title: "Require password to mount hard drive volumes?"
date: 2010-07-15
forum: General Help
---

### Post by Rallg on 2010-07-15
With my previous Ubuntu installation, I had it set up so that other partitions on the hard drive (such as Windows C: drive) could not be mounted without password.

I just noticed that in 10.04, any partition will mount without password. For me, this is not desirable.

What do I need to change, so that any request to mount a partition will require my password? If the change also affect removable media, that would be a nuisance, but I can tolerate it.

---

### Post by mike555 on 2010-07-15
I don't think restricted users can mount partitions without admin password ..

---

### Post by Rallg on 2010-07-15
I am the admin! Until recently, drive C (Windows) would not mount unless I provided my admin password. Now, it mounts on my request without first asking for my (admin) password.

I want to make it HARDER to mount C, not easier.

---

### Post by sidewalkcynic on 2010-07-15
try:

 gconf-editor

/apps/nautilus/preferences

---

### Post by Rallg on 2010-07-15
> **sidewalkcynic said:**
> try:

 gconf-editor

/apps/nautilus/preferences

That would be if I wanted to change automount for media when inserted (such as USB). But here I am talking about C partition on the hard drive. It does not automount, but mounts without requesting my admin password when requested.

It was once the case (previous Ubuntu) that C would not mount, even for the administrative user, without first requesting a password (the way that sudo works in Terminal).

After searching around, it seems to be the case that I need to enter some sort of policy file with root privileges. But everything I've seen so far is for the purpose of making it easier to mount partitions, rather than harder.

Neither fstab nor mtab does the trick.

---

### Post by Directive 4 on 2010-07-15
> **mike555 said:**
> I don't think restricted users can mount partitions without admin password ..


physical access equals root access.

---

### Post by Rallg on 2010-07-16
Marked as solved. The solution is in reply #4 here:

[http://ubuntuforums.org/showthread.php?t=1467629](http://ubuntuforums.org/showthread.php?t=1467629)

---

