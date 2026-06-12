---
title: "Claws 3.7.x - Reposity in Synaptic"
date: 2009-10-29
forum: General Help
---

### Post by Branta on 2009-10-29
Kiwi which is an Ubuntu distro

What repository do I put in or enable in Synaptic so I can install Claws 3.7.x Email client?


---
Bob

---

### Post by kellemes on 2009-10-29
> **Branta said:**
> Kiwi which is an Ubuntu distro

What repository do I put in or enable in Synaptic so I can install Claws 3.7.x Email client?


---
Bob

Do you know on what version of Ubuntu your Kiwi-system is based?

---

### Post by ikisham on 2009-10-29
[Here]("https://launchpad.net/~claws-mail/+archive/ppa") you'll have the latest Claws mail (3.7.3) for any Ubuntu.
If you use Karmic there's no need for it since it has 3.7.2 in repos.

---

### Post by kellemes on 2009-10-29
Assuming you're using Kiwi 9.04 you need to use the following repositories..
```
deb http://ppa.launchpad.net/claws-mail/ppa/ubuntu jaunty main 
deb-src http://ppa.launchpad.net/claws-mail/ppa/ubuntu jaunty main 

```

To verify it's authenticity open a terminal-window and enter..
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5ED1D082
sudo apt-get update
```

claws-mail (3.7.3-1) and claws-mail-extra-plugins (3.7.3-1) should now be available.

---

### Post by Branta on 2009-10-29
kiwilinux-9.04
built on Ubuntu 9.04 - the Jaunty Jackalope
                

I pasted into the Synaptic repository by copying this:

```
deb http://ppa.launchpad.net/claws-mail/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/claws-mail/ppa/ubuntu jaunty main
```

into the Third Party Software repository where they were listed as (no deb or deb-src):

```
http://ppa.launchpad.net/claws-mail/ppa/ubuntu jaunty main
http://ppa.launchpad.net/claws-mail/ppa/ubuntu  jaunty main (source code)
```

From terminal I executed:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5ED1D082

```

and get the error listed at the bottom:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5ED1D082
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 5ED1D082
gpg: requesting key 5ED1D082 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
```

It errors in the same way whether I Reload the repository in Synaptic or not.


---
Bob

---

### Post by kellemes on 2009-10-30
Try to use another public keyserver..
So replace "keyserver.ubuntu.com" with another keyserver and see if that works..
Pick one from the list at the bottom of the page.
[http://www.rossde.com/PGP/pgp_keyserv.html]("http://www.rossde.com/PGP/pgp_keyserv.html")

---

### Post by Branta on 2009-10-30
I used pgp.mit.edu and it worked.

3.7.3 is installed!

Thank You,

---
Bob

---

