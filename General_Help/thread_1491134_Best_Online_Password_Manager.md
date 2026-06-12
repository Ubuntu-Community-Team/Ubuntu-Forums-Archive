---
title: "Best Online Password Manager"
date: 2010-05-23
forum: General Help
---

### Post by lunatico on 2010-05-23
Hello!

I would like to start this thread to get people's opinions and suggestions. It's not an Ubuntu specific question, but I'm sure I'll find people here with good answers and suggestions.

What online password managers are out there?

I'm looking for something easy and safe that will keep all my usernames/passwords (and links) that I can access from any computer at any time. Not dependent on browser (plugin is ok) or operating system.

After googleing a bit I found this:
[http://www.passpack.com/en/home/](http://www.passpack.com/en/home/)

Looking forward to your opinions.
Thanks!

---

### Post by mac9416 on 2010-05-23
Hi, lunatico,

I know you're looking for a web-based solution, but let me suggest an offline alternative. 

I use [KeePass]("http://keepass.info/") to create and store passwords. I carry the .kdb file on a flash drive containing a [KeePass Portable App]("http://portableapps.com/apps/utilities/keepass_portable") for Windows and the .debs to install KeePass on *buntu machines; but if you'll only be needing the passwords on online machines, installation is much easier with apt-get.

I hesitate to trust anyone but myself with my passwords. That's why I prefer an offline solution.

Just my two cents.  :)

---

### Post by lunatico on 2010-05-23
> **mac9416 said:**
> I know you're looking for a web-based solution, but let me suggest an offline alternative.

That is a very good suggestion! I do carry a flash drive with me most of the time so it's definitively something I'll look into.

Thanks very much!

---

### Post by lunatico on 2010-05-26
> **mac9416 said:**
> ... and the .debs to install KeePass on *buntu machines...

Where did you got the .debs from? I couldn't find them.

I already installed with aptitude and looks pretty cool.

Thanks!

---

### Post by mac9416 on 2010-05-26
I actually downloaded the debs using [Keryx]("http://keryxproject.org") and the Karmic default project (you can get the default projects from Keryx's [download page]("http://keryxproject.org/download")). That way I know I have all the debs necessary to install on most Karmic machines.

It may be easier for you to get the debs from /var/cache/apt/archives, where Aptitude downloaded them before installing them. You may have to read dpkg's logs at /var/log/dpkg.log to find out what packages were needed to install KeePass.

The first method is better, the second is probably easier.  :)

---

### Post by Andavane on 2011-08-27
Passpack works great for me and there's an offline version too which syncs up with your online one. The tech support guys there are great too, and you'll get individual help if stuck (assuming that you've searched the FAQs).

Mind you, I've heard nothing but positive things about keepass, and I'm tempted to try that one as well, so I can use it and decide which one I prefer!

---

### Post by Habitual on 2011-08-27
Lastpass - ff addon that can also be used in mobile fashion.

---

### Post by Duncan Williams on 2011-08-27
lastpass is available for most browsers (ie/chrome, chromium, ff, opera, safari)
Is absolutely brilliant and will do all you ask...
[http://lastpass.com/](http://lastpass.com/)

---

