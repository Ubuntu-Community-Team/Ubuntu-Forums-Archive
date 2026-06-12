---
title: "Default Super User?"
date: 2006-03-26
forum: General Help
---

### Post by Tyler5690 on 2006-03-26
Is there anyway to make my account a super user so I don't have to run commands with "su" or "sudo" and so I don't have to enter a password in order to change the system clock and other such things?

---

### Post by Barrakketh on 2006-03-26
I'm confident that the answer is no.  That would be very, very bad from a security standpoint.

---

### Post by Prospero2006 on 2006-03-26
I run everything as root myself. 
The sudo thing ticks me off.  I don't need it in my life.
Now, I am also behind two firewalls and I store everything that is worth a damn
on a network server that is backed up every 24 hours. Having said that, 
here's what you do.

sudo passwd root
   -set a root password

sudo chmod 777 /etc/kde3/kdm/kdmrc

open /etc/kde3/kdm/kdmrc in a text editor.

Search for the word 'root.'
The second instance of it in that file reads something like this:
Allow Root Logins=False

--Change it to true--

ctrl-alt-backspace to restart X and login as root.

Don't be a little girl. Login as root!

Pros

---

### Post by codejunkie on 2006-03-26
[QUOTE=Tyler5690]Is there anyway to make my account a super user so I don't have to run commands with "su" or "sudo" and so I don't have to enter a password in order to change the system clock and other such things?[/QUOTE]
here's how you can do it, but you risk doing damage to your system, so do it at your own risk. open a terminal and enter 
```
sudo adduser yourusername sudo
```enter your password if it asks for it and then you shouldn't be asked for your password anymore.

---

