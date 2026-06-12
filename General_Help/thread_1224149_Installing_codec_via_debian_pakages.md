---
title: "Installing codec via debian pakages"
date: 2009-07-27
forum: General Help
---

### Post by crystaldart on 2009-07-27
Hi,
I am New to Linux.  Just loaded Ubuntu 8.1 OS in my PC. Done updating through internet.

Now I want to load Ubuntu on another PC without net facility. 

Please tell me how can I do the necessary updates Manualy. 
Also like to install Multimedia codec in the Second PC by first downloading the pakage 

Can I, in some way, use the updates from my First PC (Which is updated through Internet) ?

Thank you all

---

### Post by kerry_s on 2009-07-27
your best bet is to hook up that computer to the internet.
otherwise use a distro with all that stuff already such as mint.
[http://www.linuxmint.com/](http://www.linuxmint.com/)

---

### Post by mthalis on 2009-07-27
you can create local reposiory 

If you're looking for multimedia plugging read this
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by nikhilk on 2009-07-27
> **crystaldart said:**
> Can I, in some way, use the updates from my First PC (Which is updated through Internet) ?

The downloaded pacakges are kept in the directory "/var/cache/apt/archives". You can use them to create a local repository, some links I found on the local repository topic are [this]("http://ubuntuforums.org/showthread.php?t=20217"), [this]("http://ubuntuforums.org/showthread.php?t=42862") and [this]("http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/").

---

