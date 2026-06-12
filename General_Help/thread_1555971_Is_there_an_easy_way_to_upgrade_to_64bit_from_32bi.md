---
title: "Is there an easy way to upgrade to 64bit from 32bit?"
date: 2010-08-18
forum: General Help
---

### Post by physic.dude on 2010-08-18
I currently have Ubuntu running in 32 bit with pae but I now want to switch to 64 bit. all of my hardware supports it. Is there an easer way to switch without needing to install Ubuntu all over again? It's such a haste to copy all of my files and reinstall programs and there settings manually.

---

### Post by howefield on 2010-08-18
> **physic.dude said:**
> Is there an easer way to switch without needing to install Ubuntu all over again?

Afraid not, it is a clean install that's required.

---

### Post by physic.dude on 2010-08-19
Well, is there any utilities I can use to backup and restore everything at once?

---

### Post by lukeiamyourfather on 2010-08-19
> **physic.dude said:**
> Well, is there any utilities I can use to backup and restore everything at once?

Most of what you need is in your home directory unless you've manually stored files somewhere else. As for applications, you'll need to reinstall those again.

---

### Post by oldfred on 2010-08-19
When I converted from Jaunty I went from 32bit to 64bit with Karmic. I had 32bit and upgraded in place for several years, so I had lots of cruft. I needed the housecleaning. I also bought a new drive to give me lots of room to work.

You can move /home to a separate partition. I also then moved all data folders to /data to allow use in multiple systems but not share /home. I tried to copy all the custom system settings I made in /etc (others say backup all of /etc) to a separate folder in /home. I then made a list of all installed programs and used that to reinstall. But my installed programs included many older apps that I was not using anymore, so houseclean before making your list.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

To move /home uses rsync  (cp with -a should also work):
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by oldos2er on 2010-08-19
If you have /home on its own partition, your program settings will be saved (just remember not to format it). If not, you might want to consider creating a /home partition when you install 64-bit. [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Vaphell on 2010-08-19
synaptic allows to dump the list of installed packages to a file and later import it.

[http://geekyninja.com/archives/clone-an-ubuntu-debian-based-system-using-synaptic-markings/](http://geekyninja.com/archives/clone-an-ubuntu-debian-based-system-using-synaptic-markings/)

don't forget to check 'save full state'

---

### Post by physic.dude on 2010-08-19
I suppose I should just go for it now.

I hope I don't screw anything up...
 :-({|=

---

### Post by physic.dude on 2010-08-19
Actually, I will wait until Ubuntu 10.10 comes out because I usually find various problems and end up re installing Ubuntu after the update.

---

### Post by lukeiamyourfather on 2010-08-20
> **physic.dude said:**
> Actually, I will wait until Ubuntu 10.10 comes out because I usually find various problems and end up re installing Ubuntu after the update.

If you plan to use the installation for a while (several years) I'd go with the current 10.04 release since its an LTS release.

---

### Post by physic.dude on 2010-08-20
I always want the most up to date system, so whenever a new Ubuntu release comes out I wouldn't hesitate to get it. Whats the benefit of LTS (Long Term Support) anyway, will 10.10 have it?

---

### Post by lukeiamyourfather on 2010-08-20
> **physic.dude said:**
> I always want the most up to date system, so whenever a new Ubuntu release comes out I wouldn't hesitate to get it. Whats the benefit of LTS (Long Term Support) anyway, will 10.10 have it?

Every two years Ubuntu is an LTS release. The current LTS version is 10.04 and the last was 8.04 which is still supported. What makes it unique is three years of support and security updates for desktop and five years for server. Ubuntu 10.10 will not be LTS and has a much shorter support period, though not an issue if you reinstall or upgrade frequently.

If you want the latest all the time then LTS is not for you. If you want a system that you can setup and use for three years without much fuss of upgrading and reinstalling then LTS is the way to go.

---

