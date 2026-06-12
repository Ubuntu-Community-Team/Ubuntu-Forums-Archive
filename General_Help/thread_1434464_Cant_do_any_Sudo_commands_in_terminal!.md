---
title: "Cant do any Sudo commands in terminal!"
date: 2010-03-20
forum: General Help
---

### Post by ahl395 on 2010-03-20
Hello again everybody :)

I was following a guide to stop Ubuntu from always asking the root password. And apparently i messed something up in vsudo edit or something like that i was in...

So now when i put in a sudo command i get this...

> >>> /etc/sudoers: syntax error near line 18 <<<
sudo: parse error in /etc/sudoers near line 18
sudo: no valid sudoers sources found, quitting


so i cant even get back to undo what i edited :(

Can anyone help me please? i really dont want to reinstall...
Thanks in advance :)

---

### Post by nothingspecial on 2010-03-20
reboot and hold down shift.

Boot into a root recovery shell.

Undo what you did.

---

### Post by sisco311 on 2010-03-20
Always use **visudo** to edit the sudoers file. visudo edits the sudoers file in a safe fashion, locks the sudoers file against multiple simultaneous edits, provides basic sanity checks, and **checks for parse errors**.

---

### Post by RTrev on 2010-03-20
I'm not certain, but I think something has changed with sudo.  After updating this morning, it's been a very long time since I've been asked for a password when running things like update manager or synaptic.

It will ask me for a password if I'm in a terminal and use sudo, but if I'm in the menu system it just runs the application.  I'll start timing it now and see how long it is before I'm again asked for a password to run Synaptic.

Anyone else seeing this?

Edit: My apologies.. I'm in the wrong area.  My problem is with the beta of Lucid.  Not sure how I did this, or how to undo it!

---

### Post by sisco311 on 2010-03-20
> **RTrev said:**
> I'm not certain, but I think something has changed with sudo.  After updating this morning, it's been a very long time since I've been asked for a password when running things like update manager or synaptic.

It will ask me for a password if I'm in a terminal and use sudo, but if I'm in the menu system it just runs the application.  I'll start timing it now and see how long it is before I'm again asked for a password to run Synaptic.

Anyone else seeing this?

Edit: My apologies.. I'm in the wrong area.  My problem is with the beta of Lucid.  Not sure how I did this, or how to undo it!

You can invalidate the user's timestamp with:
```
sudo -k
```

The default timestamp timeout, in Ubuntu, is set 15 minutes:
```
sudo sudo -V
sudo sudo -V | grep "Authentication timestamp timeout:"
```

---

### Post by ahl395 on 2010-03-20
Ok holding shift didnt do anything, but i went into the recovery mode shell, and got the same message as i posted above.

---

### Post by sisco311 on 2010-03-20
> **ahl395 said:**
> Ok holding shift didnt do anything, but i went into the recovery mode shell, and got the same message as i posted above.

In the recovery mode you are logged in as root. Type:
```
visudo
```to edit the file.

---

### Post by slakkie on 2010-03-20
as root (in single user mode):

cp /etc/sudoers /etc/sudoers.borked

Make sure your user is in the admin group (groups $youruser) will show you in which groups you are.

vi /etc/sudoers

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
%admin   ALL=(ALL) ALL

```

Save, reboot and start using visudo from this moment onwards.

---

### Post by ahl395 on 2010-03-21
Thank you all so much! it worked :D

---

