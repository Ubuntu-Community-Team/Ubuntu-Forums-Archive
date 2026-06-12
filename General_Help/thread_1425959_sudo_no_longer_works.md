---
title: "sudo no longer works"
date: 2010-03-09
forum: General Help
---

### Post by gniss on 2010-03-09
When I try to use sudo, instead of asking me for my password, it simply pauses and then says 'Sorry, try again' 3 times and then gives up. It might be a clue that /dev/tty is strange, see below. Any help much appreciated. I would like to know how to fix and also what it is I might have done to produce this situation.

hm@mineralmentor:~$ sudo echo 1
Sorry, try again.
Sorry, try again.
Sorry, try again.
sudo: 3 incorrect password attempts
hm@mineralmentor:~$ 



hm@mineralmentor:~$ cat /dev/tty
Password:ew password: 

hm@mineralmentor:~$

---

### Post by Iowan on 2010-03-09
[This]("http://www.psychocats.net/ubuntu/fixsudo") is a page about fixing **sudo** - hope it helps.

---

