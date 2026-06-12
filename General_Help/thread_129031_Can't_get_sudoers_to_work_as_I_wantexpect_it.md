---
title: "Can't get sudoers to work as I want/expect it"
date: 2006-02-12
forum: General Help
---

### Post by raphha on 2006-02-12
Hello everyone,

well, I hope someone can explain me, what's wrong with my sudoers file or my understanding:
I'd like to allow user "user1" to execute the comand "/sbin/ifconfig" without promting for a password. So I added a few lines via "visudo" and commented out the defaults (to be sure they don't interfere with what I want to do). The resulting sudoers file looks like this:

-snipp-
# Cmnd alias specification
Cmnd_Alias QEMU=/sbin/ifconfig

# Defaults

#Defaults       !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
user1  ALL=NOPASSWD: QEMU
#user1 ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
-snap-

Anyways, everytime I try to run "sudo /sbin/ifconfig" (as user1 of course) I do still have to enter my password - but why? :-k 

I'd really appreciate any hints...

thanks,
raph

---

### Post by dresnu on 2006-02-12
I'm no expert and I actually might be stating a stupidity :mrgreen: , but why do you have to create an alias for the command? Why don't you just try ```
user1 ALL=NOPASSWD: /sbin/ifconfig
``` and removing the "Cmnd_Alias QEMU=/sbin/ifconfig" line?

---

### Post by raphha on 2006-02-13
thanks for your try, but unfortunately that doesn't solve the problem... I also double and tripple-checked the path to the command and it's all right
well, I am really clueless - anyone else any ideas?

thank you anyways, regards, raph

---

### Post by ovichi on 2006-10-09
I got the same problem: it seems that sudo ignores /etc/sudoers->NOPASSWD  for the **main user** (the one you use as administrator with "sudo -i"). If you give sudo perm to a new created user it works... 
So the "main user" capability of becoming root is incompatible with NOPASSWD? should I look in pam.d? :confused:

---

### Post by ovichi on 2006-10-16
I found it: since /etc/sudoers is parsed in "one pass" you must put your chenges AFTER:

 %admin ALL=(ALL) ALL

.....NOPASSWD: commands

Now it works as you expect.:mrgreen:

---

### Post by raphha on 2006-10-16
I'll try that... that's really cool to get a reply after so many month :)
will come back with my results,
so long,raph

---

### Post by raphha on 2006-10-16
Yesss, now it works! Thank you very much...

one question about your explanation: is it right, that bebause I am in the admin group my rights have been removed/reset again by the %admin-line? So this file works like "last applicable line rules"?

raph

---

### Post by j3cakes on 2006-11-19
I'm having the same problem: it keeps asking me for a password. Can anyone help?

I'm trying to get around this bug with samba by putting the "samba restart" command in the startup sequence. I'm not sure it will work but it's better than having to cart my monitor up the stairs each time I have to reboot this thing (vnc doesn't work after rebooting edgy either.)

Anyway, I've pasted the sudoers here. Can someone please help?

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

#Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

user1 ALL=NOPASSWD: /etc/init.d/samba restart

---

