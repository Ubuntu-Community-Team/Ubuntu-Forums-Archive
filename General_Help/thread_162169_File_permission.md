---
title: "File permission"
date: 2006-04-18
forum: General Help
---

### Post by Defscanguci on 2006-04-18
There are a lot of files I need to edit as a non-root user, but I am constantly warned that I cannot edit them because I do not have permission (like the start-up modules file, the userchrome file for FireFox, etc).

How do I get permission to edit these and any files?

---

### Post by aysiu on 2006-04-18
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by jazzmuzik on 2006-04-18
Just insert 'sudo' in front of the command. It means 'superuser do'. When asked for a password type your user password:

sudo synaptic
sudo gedit /etc/fstab
sudo vi /etc/fstab

---

### Post by aysiu on 2006-04-18
[QUOTE=jazzmuzik]
sudo synaptic[/QUOTE] If you're launching Synaptic, I'd advise ```
gksudo synaptic
```

---

### Post by jazzmuzik on 2006-04-18
[QUOTE=aysiu]If you're launching Synaptic, I'd advise ```
gksudo synaptic
```[/QUOTE]

What's the difference between sudo and gksudo?

---

### Post by aysiu on 2006-04-18
[QUOTE=jazzmuzik]What's the difference between sudo and gksudo?[/QUOTE] There are a couple--the most immediate is how they ask for the password.

If you use ```
gksudo synaptic
``` a little graphical pop-up will ask for your password. If you use ```
sudo synaptic
``` you'll be asked for your password in the terminal. So ```
gksudo synaptic
``` is obviously more appropriate for a launcher button or keyboard shortcut.

Also, sometimes it's the case that using *sudo* on certain graphical applications affects the permissions of local user files (configuration files) in a bad way.

However, *sudo* does tend to be more secure. For example, if you type *sudo blahblahblah* in a terminal and then open a new terminal and type *sudo gibberish*, you'll be asked for a password in that second terminal, even though the timeout in the first terminal hasn't ended.

If you use *gksudo blahblahblah* and then run *gksudo gibberish*, you will not be asked for a password for *gibberish* if it's within the timeout period from when you first launched *blahblahblah*.

---

### Post by jazzmuzik on 2006-04-18
It sounds like sudo is for the terminal and gksudo is for a gui program launch, like Alt-F2.

---

### Post by aysiu on 2006-04-18
[QUOTE=jazzmuzik]It sounds like sudo is for the terminal and gksudo is for a gui program launch, like Alt-F2.[/QUOTE] That's the long and short of it. Well, the short, anyway.

---

