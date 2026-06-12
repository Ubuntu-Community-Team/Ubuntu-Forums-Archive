---
title: "Where Should I place the Joomla folder?"
date: 2010-10-17
forum: General Help
---

### Post by trupokarudos on 2010-10-17
[B]I've installed Lampp and I wanna install also Joomla.
Where should I place Joomla folder?
the tutorials say var/www but this folder does not exist.
some greek users told me to put the folder in the public_html folder- but this way it doesnt work!
What shall I do?[/B]

---

### Post by trupokarudos on 2010-10-17
nobody again???

---

### Post by sandyd on 2010-10-17
> **trupokarudos said:**
> I've installed Lampp and I wanna install also Joomla.
Where should I place Joomla folder?
the tutorials say **/**var/www but this folder does not exist.
some greek users told me to put the folder in the public_html folder- but this way it doesnt work!
What shall I do?
your missing a slash

---

### Post by trupokarudos on 2010-10-17
Hmmm 
I didnt understand (my english aren't well).
Can you be more specific?

---

### Post by sandyd on 2010-10-17
> **trupokarudos said:**
> Hmmm 
I didnt understand (my english aren't well).
Can you be more specific?
Compare the quote I did in the 3d post and the post you did in the first post.
--------------------------------------------------------------------
First Post
> **trupokarudos said:**
> I've installed Lampp and I wanna install also Joomla.
 Where should I place Joomla folder?
 the tutorials say var/www but this folder does not exist.
 some greek users told me to put the folder in the public_html folder- but this way it doesnt work!
 What shall I do?

Second Post
> **trupokarudos said:**
> I've installed Lampp and I wanna install also Joomla.
 Where should I place Joomla folder?
 the tutorials say **/**var/www but this folder does not exist.
 some greek users told me to put the folder in the public_html folder- but this way it doesnt work!
 What shall I do?

---

### Post by trupokarudos on 2010-10-17
Ok!
:-)
Do you have any ideas?

---

### Post by sandyd on 2010-10-17
> **trupokarudos said:**
> [B]I've installed Lampp and I wanna install also Joomla.
Where should I place Joomla folder?
the tutorials say var/www but this folder does not exist.
some greek users told me to put the folder in the public_html folder- but this way it doesnt work!
What shall I do?[/B]

> **trupokarudos said:**
> Ok!
:-)
Do you have any ideas?
should be /var/www not var/www

---

### Post by trupokarudos on 2010-10-17
This folder does not exist.
It does exist if you install appache2 and mysql instead of Lampp.
When you install Lampp you should put joomla somewhere else.
but where?
The above mistake was only a mistake in typing...

---

### Post by sandyd on 2010-10-17
> **trupokarudos said:**
> This folder does not exist.
It does exist if you install appache2 and mysql instead of Lampp.
When you install Lampp you should put joomla somewhere else.
but where?
The above mistake was only a mistake in typing...
theirs a reason why theirs this notice on the site.
> [B]Welcome to the Linux version of XAMPP
(on x86-compatible processors)[/B]  By the way: **In the past this software was called LAMPP but to avoid  misconceptions we renamed it to »XAMPP for Linux«**. So if you are seeking  for LAMPP you're on the right track. ;)

**L**INUX, **A**PACHE, **M**YSQL,** P**HP
is more commonly refered to, which is why they changed the name in the first place.

the correct direcotyr should be 
/place/where/you/installed/xampp/htdocs

---

### Post by trupokarudos on 2010-10-18
thanks

---

