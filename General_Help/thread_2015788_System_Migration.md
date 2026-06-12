---
title: "System Migration"
date: 2012-07-03
forum: General Help
---

### Post by jacobroecker on 2012-07-03
Hi all!  I'm getting a System76 machine with U 12.04 installed to replace an old IBM T40 with U 10.04 that I've got running as a server.  My internet is terribly slow (15kbps) and I'm wondering if there's a way to move Apache2, MySQL, and the other server apps over from the 10.04 machine without having to redownload/reinstall them from the web.  Is it as simple as copying the apache2 folder into /etc?

I know there are tools to clone a drive, but since I'm upgrading from one version to another I don't necessarily want to to that, I just need to move my apps over from one machine to the next.

I'm sure I'm probably better off reinstalling the apps and reconfiguring them (and it would be good practice), but I've got to believe there's another option out there I could at least consider before I spend a day waiting for things to download.

Thanks in advance!

---

### Post by msammels on 2012-07-03
Hey Jaco,

First of all kudos on the System76! Also, as for your question, the only way I can think of would be cloning it. As far as I am aware, direct copy/paste would fail since your LAMP server would be configured for a different computer. However, there are two very simple ways to download LAMP in Ubuntu 12.04 now. The first way is like so:

```
sudo apt-get install lamp-server
```

Or the other way is to do it through taskel:

```
sudo apt-get install taskel
sudo taskel
```

And select it from the list which appears. This shuoldn't take too long to download.

---

