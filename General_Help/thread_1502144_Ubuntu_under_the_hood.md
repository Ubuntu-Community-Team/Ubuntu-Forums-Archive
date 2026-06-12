---
title: "Ubuntu under the hood"
date: 2010-06-05
forum: General Help
---

### Post by freqhz on 2010-06-05
Hello! I want to get some books or info about internals of  Ubuntu. There are a lot of Ubuntu books now but many of them simply teach how to accomplish a particular task using GUI. Usually these books include huge numbers of screenshots with a text like "Click here to do smth". That isn't what I need. I'm interested in examining Ubuntu OS from the kernel and configuring it via command line, editing configuration files, etc. 
On the topic of kernel programming I've bough the book "Understanding the Linux kernel" 3rd edition. But I can't find appropriate book on Ubuntu internal structure. 

Thanks a lot!

---

### Post by dv3500ea on 2010-06-05
Ubuntu is based on Debian and uses the GNOME Desktop Environment. Look up areas such as:
[LIST]
[*]The Debian package management system (apt)
[*]LSB 
[*]x.org
[*]XDG and freedesktop.org
[/LIST]

I don't know of any specific books available but if you search you should be able to find relevant wikis.

---

### Post by XubuRoxMySox on 2010-06-05
There's also a "minimal Ubuntu" installation CD that installs only the base system with a CLI. That way you could explore it and try out some of the stuff in the book!

Debian has a "netinstall" CD too that lets you build your own Debian in the same way, and it avoids alot of the Gnome stuff that Ubuntu depends on (too much, arguably, but that's a whole 'nother subject).

have fun,
Robin

---

