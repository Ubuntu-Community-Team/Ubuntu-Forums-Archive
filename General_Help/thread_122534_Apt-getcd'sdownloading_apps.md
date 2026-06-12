---
title: "Apt-get/cd's/downloading apps"
date: 2006-01-27
forum: General Help
---

### Post by Uncle Che on 2006-01-27
I am sorry for the cryptic title to this topic, but here is the help I need:

I need to know if it is possible/easy to make a CD of a bunch of apps that I can get over apt-get. 

Here is the deal:
I have 30 school computers that I want to put Ubuntu Linux on in a dual boot environment. They have net access but it is very very very slow. Updating each computer individually with the software I want on them would take me forever. 

So I am curious if I can download the apps that I want from the web and burn a CD for them? How would I do this and could I still use apt-get because it makes it so easy and would love for the kids to see how easy it is. 


Thanks in advance,
Uncle Che

---

### Post by adwait on 2006-01-27
If there are only a few apps that you would like to download, simply download their .deb files and then install from the CD on each computer using
```
sudo dpkg -i <wahtever>
```

---

### Post by Uncle Che on 2006-01-27
yeah I thought about doing that, but there are many that I would like to and I want to introduce the students to apt-get as well. It is the most exciting thing about Ubuntu Linux.

---

### Post by Burke on 2006-01-27
I would suggest having a look at the directory structure of the install CD. The default installation uses it as a repository, so one could logically conclude that you could replicate that, if you just added it to /etc/apt/sources.list

EDIT: That actually looks like a LOT of work.

---

### Post by az on 2006-01-27
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

Use the cd to make a local repository for all of the computers (are they networked together?)  Then have each of the other computers only use the local repo as their apt source.  You can control all of the computers and their updates by manipulating your local repository.

---

### Post by Uncle Che on 2006-01-27
wow this is why Ubuntu is the best, the perfect answer I was looking for to what I thought was a complicated question in less than 2 hours!

It looks like the wiki article is a lot of work, but it looks pretty straightforward and with all things Ubuntu, just try it and you will be able to do it. 

\\:D/

---

