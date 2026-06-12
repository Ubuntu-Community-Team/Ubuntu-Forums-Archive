---
title: "Why am I getting this error?"
date: 2006-06-10
forum: General Help
---

### Post by nami on 2006-06-10
Hi

Anyone know why I'm getting this error message?

[[IMG]http://img123.imageshack.us/img123/751/screenshot1wz.th.png[/IMG]](http://img123.imageshack.us/img123/751/screenshot1wz.png)

nami

---

### Post by thasheep on 2006-06-10
You need to enable the multiverse repository. Use synaptic or add 'multiverse' to one of the deb lines (after main, universe, etc) in /etc/apt/sources.list

---

### Post by steve.horsley on 2006-06-10
No idea. It's not very helpful, is it? Try installing liblame and see what error you get then.

---

### Post by blackjack6.21.91 on 2006-06-10
Post the contents of your sources.list here.  You can view them by punching this into a terminal:

sudo gedit /etc/apt/source.list

---

### Post by nami on 2006-06-10
Here is my source.list:

[[IMG]http://img104.imageshack.us/img104/4448/sourceslist0vg.th.jpg[/IMG]](http://img104.imageshack.us/img104/4448/sourceslist0vg.jpg)

And this is what happens when I search for liblame from synaptic manager:

[[IMG]http://img145.imageshack.us/img145/833/liblame5rb.th.jpg[/IMG]](http://img145.imageshack.us/img145/833/liblame5rb.jpg)

---

### Post by deb2006 on 2006-06-10
liblame0 is not there and therefore it is not installable. Which in return is the reason why you cannot install gstreamer0.10-plugins-ugly-multiverse ;)

---

### Post by jocko on 2006-06-10
As far as I can see you haven't enabled multiverse.

I think it would work if you made your sources.list look like this:
```

deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb http://www.compiz.info/ dapper main
deb-src http://www.compiz.info/ dapper main
```

---

### Post by nami on 2006-06-10
Thanks, figured it out today!

---

