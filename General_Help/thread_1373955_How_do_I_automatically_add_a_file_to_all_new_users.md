---
title: "How do I automatically add a file to all new users?"
date: 2010-01-06
forum: General Help
---

### Post by velosprinter on 2010-01-06
I am making a live CD and need to add a config file to all new users Home folder. This includes the Ubuntu user in the Live CD and New users created on install from the live CD. 

Path would be: /home/ubuntu/config.file

---

### Post by i.r.id10t on 2010-01-06
Put it in /etc/skel

---

### Post by Saghaulor on 2010-01-06
> **i.r.id10t said:**
> Put it in /etc/skel

I don't think that this will entirely accomplish what the OP is asking.

Any files added to /etc/skel will be added to new user profiles when using ```
useradd
``` to add new users. I'm not sure that it will add the files from /etc/skel when adding users using other commands.

Additionally, when packaging your own livecd (something I know nothing about) putting the files in /etc/skel will not copy the files to the default live user profile, those must be copied separately. 

Here is a write up on the /etc/skel directory.

[http://www.linuxhowtos.org/Tips%20and%20Tricks/using_skel.htm]("http://www.linuxhowtos.org/Tips%20and%20Tricks/using_skel.htm")

---

### Post by velosprinter on 2010-01-06
/etc/skel did the trick for adding the file. I see it in the Live CD and will do an HD install later. 
Thank you very much!

---

