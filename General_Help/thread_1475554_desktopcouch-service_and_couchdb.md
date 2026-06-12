---
title: "desktopcouch-service and couchdb??"
date: 2010-05-07
forum: General Help
---

### Post by Grone1985 on 2010-05-07
Hi, I'm running Lucid and have a question about this two processes, if I have no gwibber accounts setup why do I have two instances of this two processes running? Is that normal?

Cheers!

---

### Post by Grone1985 on 2010-05-09
bump

---

### Post by Skybinary on 2010-06-29
i have these in processes, just wondering what they are.

---

### Post by timuckun on 2010-08-10
bump

---

### Post by mishaokami on 2011-02-01
[http://wiki.apache.org/couchdb/Frequently_asked_questions](http://wiki.apache.org/couchdb/Frequently_asked_questions)

So... it looks like a database that stores data relevant to a given users session.  Why that means that it has many SSL connections to canonical.com (check netstat) i have no idea.

As to what data it stores look at the dev blog below.  Contacts in evolution are just one example.
[http://blogs.gnome.org/rodrigo/category/couchdb/](http://blogs.gnome.org/rodrigo/category/couchdb/)

Any data stored in a couchdb can also be replicated on UbuntuOne.

m

---

### Post by rashblood on 2011-09-11
I just remove the apache couchdb,with command:
sudo rm -rf /usr/lib/desktopcouch
and reboot the system.
:D

---

