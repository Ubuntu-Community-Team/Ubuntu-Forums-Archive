---
title: "Why is MySQL needed?"
date: 2010-10-20
forum: General Help
---

### Post by adamjkok on 2010-10-20
Why does (almost) every PHP script require MySQL? It's a *major* pain to go into PhpMyAdmin and create a new database, then a new user, and then use Keepassx to keep track of the passwords...

Why not use XML files? Can someone explain the advantages?

---

### Post by lavinog on 2010-10-20
For one, XML files are much slower to manipulate.

Having a centralized process handling queries is more efficient than having hundreds of scripts processing text files.

The data in mysql is also stored in a format that consumes less space.  Mysql can delegate requests so that one request doesn't interfere with another. ex: A long running query needs to finish before another query deletes everything.

You don't have to use PHP and mysql though, and many times you don't even need store the passwords since the php configuration files are going to have them stored in plain text.

Are you setting up websites?

You may want to consider posting in the programming section of the forums.

---

### Post by SeijiSensei on 2010-10-20
> **adamjkok said:**
> Why does (almost) every PHP script require MySQL?

I'd like to see more support for the totally-free and powerful PostgreSQL myself, especially now that MySQL is in Oracle's hands.

---

### Post by slackthumbz on 2010-10-20
PHP is evil and no self respecting admin would ever use a web based gui for server administration.

---

### Post by hrickh on 2010-10-20
> **slackthumbz said:**
> PHP is evil and no self respecting admin would ever use a web based gui for server administration.
Not all hosting packages offer shell/ssh access.

R.
==

---

