---
title: "Can I use the same home partition for 2 versions of ubuntu?"
date: 2010-06-29
forum: General Help
---

### Post by 84Taran on 2010-06-29
Hi,

I'd like to set my comp up to dual boot with lucid and the maverick alpha.  Currently I have lucid with a separate home partition.  Is it possible to have both instances of ubuntu using the same home partition? or will this corrupt it in some way?

---

### Post by burton247 on 2010-06-29
Nah thats fine. You just point home to the partion it's on when installing. And make sure you don't have it reformat it

---

### Post by supergrav on 2010-06-29
While you install maverick you can choose to mount your lucid /home partition as /home for maverick. I'm not sure if there is going to be any corruption but it seems unlikely to happen.

---

### Post by burton247 on 2010-06-29
I had about 4 linux's running on the same home on my desktop, it's fine :)

(That's my play machine btw, I don't do stuff like that normally)

---

### Post by 84Taran on 2010-06-29
cool....this could be dangerous information in my hands :) god only knows how many distros I'll end up with.

I'll mark this as solved as soon as I've installed the dual boot

---

### Post by oldfred on 2010-06-29
Those that say its is ok are assuming you create a new user ID so you really have separate data just in the same partition. 

Actually an upgrade is intended to use the same settings and upgrade them so /home but may not be backwards compatible as the new software may write info that the old version does not recognize. 

You should definitely not share across different distributions. Versions of software may be too different and hidden settings for the user may not be the same.

With multiple installs you can share data, I recommend a separate data partition.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by burton247 on 2010-06-29
I just have a folder in on /home called public. Then I symlink to folders such as music and other things that I want access to on other OS's, or even another user on the one OS.

---

