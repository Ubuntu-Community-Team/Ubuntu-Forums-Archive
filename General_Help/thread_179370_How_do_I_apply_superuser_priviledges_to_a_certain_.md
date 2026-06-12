---
title: "How do I apply superuser priviledges to a certain application?"
date: 2006-05-19
forum: General Help
---

### Post by daller on 2006-05-19
Hi There,

I'm using this project, to control my hardware:

[http://www.sourceforge.net/projects/sispm](http://www.sourceforge.net/projects/sispm)

The problem is that I need it to run without applying the superuser password!

Now I run:

sudo sispm

How do I make it work, only running:

sispm

???

---

### Post by louis_nichols on 2006-05-19
a quick google for "sudo howto" showed [this]("http://www.linuxhomenetworking.com/linux-hn/addusers.htm#_Toc92808558") among many. :)

your answer is in the lower part of the page.

---

### Post by daller on 2006-05-19
Think I messed it up:

sudo: parse error in /etc/sudoers near line 17

What do I do now?

---

### Post by Ramses de Norre on 2006-05-19
See what you changed.. there will be a erroneous syntax or typo near line 17.
What's in the sudoers file now?

---

### Post by daller on 2006-05-19
I can't access it!

I don't know root's password! - Is there a standard pass for clean-installed systems? (Can't login as root with my own pass!)

sudo vi /etc/sudoers, returns the error!

Any ideas?

---

### Post by daller on 2006-05-20
Rebooted in "Recovery mode"...

Changed the "/etc/sudoers"-file.

Inserted this line:

daniel ALL= /usr/bin/sispm

And now it seems to work!

Thank you for your help!

---

### Post by daller on 2006-05-31
This is my /etc/sudoers file:

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
elav    ALL= /usr/bin/sispm

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

```

"elav" is my username, but I can't run /usr/bin/sispm without sudo, how can that be?

I get this:

elav@ubuntu:~$ /usr/bin/sispm
usb_set_configuration: could not set config 1: Operation not permitted
sispm: device not found!

---

