---
title: "Looking for Information on privacy  and shutdown script."
date: 2009-09-05
forum: General Help
---

### Post by Nicky.. on 2009-09-05
Hi all,


Am just looking for a few points on where does Ubuntu store temp information like history/browser cache also i would like to create a script that on shut-down will rm the /tmp and any others I choose, I say rm but ill be using a bcwipe command instead if someone could steer me in the right direction that would be great.

I really just want to be able to use my beloved Ubuntu then shut it down knowing that there no browsing/file information, i work for a large company most my other colleagues use windows and they have very strict information and guidelines but i enjoy Ubuntu too much to use windows but i cant use it unless i know all information on the system is gone after i logout i dont want to use a live cd either. :(

---

### Post by imhotep59 on 2009-09-05
If your bowser is firefox, the cache is located in : /home/your_user_name/.mozilla/firefox/*name_of_profile*.default/cache

The name_of_profile looks like vf8xhelu.default (it is not vf8xhelu, of course, for your computer but it is composed of 8 characters)

---

### Post by bodhi.zazen on 2009-09-05
You can also mount your temp file in ram, using tmpfs

I do this with the firefox cache. It is a simple edit to /etc/fstab

For an example see : [http://blog.bodhizazen.net/linux/netbook-optimization/](http://blog.bodhizazen.net/linux/netbook-optimization/)

But really, have you looked at the options in firefox ?

Firefox has both private browsing and you can clear your history when you close it.

---

