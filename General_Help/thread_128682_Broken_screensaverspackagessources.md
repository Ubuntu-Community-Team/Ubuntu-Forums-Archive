---
title: "Broken screensavers/packages/sources?"
date: 2006-02-12
forum: General Help
---

### Post by Escape311 on 2006-02-12
I had everything working fine for a while until today when I was installing some different things, and now some of my screensavers are gone. More specifically the OpenGL related ones, ie: Flurry, Flip text, Atlantis. Also when I run Synaptic to install other software, it gets to the end and shows this: 
> E: msttcorefonts: subprocess post-installation script returned error exit status 1

W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No such file or directory)

Is there a way to fix this without reinstalling? I tried reinstalling xscreensaver and even Synaptic thinking that might might fix my broken packages or my source list but nothing has worked. Any advice? Thanks.

By the way, This is my first time using Ubuntu after using Xandros 3 for a while. I think so far Ubuntu is my favorite.:)

---

### Post by dcstar on 2006-02-12
[QUOTE=Escape311]I had everything working fine for a while until today when I was installing some different things, and now some of my screensavers are gone. More specifically the OpenGL related ones, ie: Flurry, Flip text, Atlantis. Also when I run Synaptic to install other software, it gets to the end and shows this: 


Is there a way to fix this without reinstalling? I tried reinstalling xscreensaver and even Synaptic thinking that might might fix my broken packages or my source list but nothing has worked. Any advice? Thanks.

By the way, This is my first time using Ubuntu after using Xandros 3 for a while. I think so far Ubuntu is my favorite.:)[/QUOTE]
The wine repository sources.list entry should probably be:

deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) breezy/

---

### Post by Escape311 on 2006-02-12
So how do I restore the repositories list? Is there a way?

By the way, when I open up Synaptic, this is the error I get:

> 
The following problems were found on your system:


W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)


What can I do?

---

### Post by bluevoodoo1 on 2006-02-12
[QUOTE=Escape311]So how do I restore the repositories list? Is there a way?

By the way, when I open up Synaptic, this is the error I get:



What can I do?[/QUOTE]

```

sudo gedit /etc/apt/sources.list

```

Add what dcstar said...

deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) breezy/

and add ## in front of the lines that you don't want or are giving you trouble.

---

