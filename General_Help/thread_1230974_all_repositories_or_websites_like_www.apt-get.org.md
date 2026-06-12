---
title: "all repositories or websites like www.apt-get.org"
date: 2009-08-04
forum: General Help
---

### Post by spikemcc on 2009-08-04
What we need now for ubuntu is a website like [www.apt-get.org](www.apt-get.org) for testers ...
They choose ubuntu cause compiling is time consuming but the repositories don't include many useful softwares or well loved games ... Even if they are there, some are outdated or don't work well ... So testers always added all ubuntu/debian repositories they need, with official softwares repositories like from miro and added multiples ppas cause ubuntu don't have what they want ...

Now help me a little and with your help, I will try to make the list we need !!!

---

### Post by CatKiller on 2009-08-04
You mean like [GetDeb]("http://www.getdeb.net/")?

---

### Post by spikemcc on 2009-08-04
Getdeb isn't a repository as I remember, just a website so you you have to go online to update your stuff and GUI interface is required ...

---

### Post by chriskin on 2009-08-04
there is a repository for getdeb.net though
check here
[http://getdeb.masio.com.mx/](http://getdeb.masio.com.mx/)

---

### Post by kpkeerthi on 2009-08-04
Have you heard of [PPAs]("https://edge.launchpad.net/ubuntu/+ppas")?

---

### Post by CatKiller on 2009-08-04
You probably ought to read [this cautionary tale]("http://ubuntuforums.org/showthread.php?t=297814") before you try to create a meta-repository with the contents of all possible repositories.

---

### Post by spikemcc on 2009-08-04
That's why I want to make a list of the more officials repositories as possible ...

a list divided in 3 types : official repo, ppa, testing (others)

---

### Post by CatKiller on 2009-08-04
I don't think you'll be able to break them down like that. The "official" repositories, everyone already has. **Everything** else is a testing repository. Even if it's Wine, even if it's Medibuntu, even if it's a PPA. The only way you'll be able to get sufficient granularity is to break it down by the actual repository itself, so that a user can choose to have non-free stuff, but not beta versions of Wine, for example. Which is exactly what we've got now.

Having some kind of front-end so that users don't have to find the individual repositories (since they probably don't know what they're looking for) might be useful in some cases, but I don't think that it would be as useful as you imagine. Especially since they're going to have to run whatever it is as root so that you can change sources.list and add keys. That's a lot of trust to put in a collection on the Internet.

---

