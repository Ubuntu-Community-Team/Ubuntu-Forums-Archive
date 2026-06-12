---
title: "HELP! I broke my sudoers file"
date: 2010-02-14
forum: General Help
---

### Post by NertSkull on 2010-02-14
So I've done bad things I think.  I have a relatively fresh install of ubuntu and was playing around with things because I'm trying to learn more about everything.

In the process I commented out (#) the %ADMIN line in the file.  Now I have lost sudo ability on my system, and because of that, I can't get back in (sudo visudo) to change that back.

I've tried the su, sudo su, and all the other things I can think of, but no luck.

Can I fix this?  Or am I re-installing?  I'm really hoping there is a way to get in still.

I thought about booting to a live CD and going in to fix it that way, but I have my entire system encrypted using LUKS, so I assume that won't work (haven't actually tried it though).

Any ideas?

:oops: :: hangs head in shame ::

---

### Post by SuperSonic4 on 2010-02-14
Use the recovery menu via grub. Frmo there drop into a root shell and edit sudoers as root

---

### Post by NertSkull on 2010-02-14
SUCCESS - Thank you!!

---

### Post by terrrorr on 2010-02-14
Have you already defined root's password ?!

If answer is no -> you are screwed
If answer is yes you could try this

after you have logged in press ALT+F2 and log in using root password (root/*root_password*). Sudoers file locates in /etc/. If you do not have it, you'll need to create it again.

```
nano /etc/sudoers
```

copy and paste or write 

```

Defaults        env_reset
root    ALL=(ALL) ALL
%admin ALL=(ALL) ALL

```

Save the file and exit. Now you could try it again.

Press CTRL+ALT+F8 to get back to desktop

default sudoers file:

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

I hope this solved your problem

---

