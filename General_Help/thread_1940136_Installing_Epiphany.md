---
title: "Installing Epiphany"
date: 2012-03-13
forum: General Help
---

### Post by TexasRussian on 2012-03-13
Okay. So for the past three hours I've been trying to install Epiphany 3.3.90.. With no success I'd decided to go to the awesome community ;) Now I'm running Ubuntu 11.10 x64 with Gnome 3.2.

Now I've tried the whole "sudo ./configure" then "make" then "make install" but it doesn't work. I get > make: *** No rule to make target `install'.  Stop.


Here is where I got it from, the .tar.xz
[http://ftp.acc.umu.se/pub/GNOME/sources/epiphany/3.3/](http://ftp.acc.umu.se/pub/GNOME/sources/epiphany/3.3/)

Anyhow if anyone could assist me and guide me through the install, that'd be really great! :D

---

### Post by Grenage on 2012-03-13
It looks like it has an installation script included:

```
chmod +x install-sh
./install-sh
```

---

### Post by TexasRussian on 2012-03-13
hmm after I tried the './install-sh' and it gave me this
> ./install-sh: no input file specified.


---

### Post by Grenage on 2012-03-13
My bad then!

What happens when you don't use sudo with configure?  Generally you only need root rights for *make install*, so perhaps it's got nothing to make because the output of configure was root-rights-only.

---

### Post by TexasRussian on 2012-03-13
Well, './configure' works but it errors at the end with:
> checking for intltool >= 0.40.0... ./configure: line 13221: intltool-update: command not found
 found
configure: error: Your intltool is too old.  You need intltool 0.40.0 or later.
but I don't know how to update it.
:(

---

### Post by Grenage on 2012-03-13
Google is your friend. ;)

[http://ubuntuforums.org/showpost.php?p=8334230&postcount=3](http://ubuntuforums.org/showpost.php?p=8334230&postcount=3)

Have you checked to see if there is a repository you could use?  It would probably make installation somewhat easier if you could just 'apt-get install epiphany'.

---

### Post by TexasRussian on 2012-03-13
Yeah, but it installs some old version. I think 3.2 :'(

---

### Post by Grenage on 2012-03-13
Add the repository:

```
sudo add-apt-repository ppa:webkit-team/ppa
sudo add-apt-repository ppa:webkit-team/epiphany
```

If epiphany is installed:

```
sudo apt-get update && sudo apt-get upgrade
```

If it is not installed:

```
sudo apt-get install epiphany-browser epiphany-browser-data&#65279;epiphany-extensions
```

---

### Post by TexasRussian on 2012-03-13
lol, that's empathy, I need epiphany, the web browser..

---

### Post by Grenage on 2012-03-13
> **TexasRussian said:**
> lol, that's empathy, I need epiphany, the web browser..

*cough*

I changed the post.

---

### Post by TexasRussian on 2012-03-13
Thanks, but, it installed version 3.2 and I need 3.3 :\

---

### Post by TexasRussian on 2012-03-13
Thanks! buuuuut, it installed 3.2 and I need 3.3... :\

---

### Post by Grenage on 2012-03-13
It looks like the gnome repo will have it:

[http://iloveubuntu.net/epiphany-web-browser-334-released-new-ui-precise-ppa-available](http://iloveubuntu.net/epiphany-web-browser-334-released-new-ui-precise-ppa-available)

However it does note that it's a work in progress.  Failing that, it's source code time again.  For the record, Google generated all of this info. ;)

---

### Post by TexasRussian on 2012-03-13
hmm, nope, went through the giant install, and still at version 3.2 I even purged epiphany and re-installed it, but back to 3.2 again..

---

### Post by Grenage on 2012-03-13
Source code time, then!

---

### Post by TexasRussian on 2012-03-13
Why do they have to make it so complicated? I mean why release all these versions if you cant freaking install them???

---

### Post by Grenage on 2012-03-13
Most likely because the latest version isn't ready for the masses.  If it *is* ready, it hasn't been tested with the current desktops, so it's not in their repositories.

Trust me, it's better than the alternative.  Imagine the carnage if an updated application trashed part of the system.

---

### Post by TexasRussian on 2012-03-13
Then why release it?

---

### Post by Grenage on 2012-03-13
> **TexasRussian said:**
> Then why release it?

They haven't, which is why you had to download source.  The gnome site lists Epiphany 3.0.x releases as stable, and Epiphany 3.1.x releases as *development*.

God only knows what that makes 3.3.

---

