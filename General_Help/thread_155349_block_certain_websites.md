---
title: "block certain websites?"
date: 2006-04-04
forum: General Help
---

### Post by bionnaki on 2006-04-04
hello. I am trying to block a certain website URL using the hosts file. I would like to block a particular page, but not the actual website. the website itself is fine, but I would like to block the pages with adult content.

for example, I would like to block [http://www.333.com/555](http://www.333.com/555) but not [http://www.333.com](http://www.333.com) itself

is this possible with the hosts file? I have tried, but so far it doesnt work.
any ideas on how I can accomplish this?

---

### Post by xXx 0wn3d xXx on 2006-04-04
[QUOTE=bionnaki]hello. I am trying to block a certain website URL using the hosts file. I would like to block a particular page, but not the actual website. the website itself is fine, but I would like to block the pages with adult content.

for example, I would like to block [http://www.333.com/555](http://www.333.com/555) but not [http://www.333.com](http://www.333.com) itself

is this possible with the hosts file? I have tried, but so far it doesnt work.
any ideas on how I can accomplish this?[/QUOTE]
Try [ this ](http://ubuntuforums.org/showthread.php?t=110440&highlight=block+ads+spyware) but with the website.

---

### Post by stoeptegel on 2006-04-04
[http://www.333.com/555/*](http://www.333.com/555/*) might work, i have removed a nasty commercial at the beginning of a newsvideo this way on rtlnieuws.nl 8)
(never seen it back for weeks)

---

### Post by bionnaki on 2006-04-04
yeah, I tried that already...but it doesnt work. hmmm

---

### Post by stoeptegel on 2006-04-04
It doesn't work instantly because there's a local DNS cache somewhere. You might have to reboot or flush it with a command which i don't know.

---

