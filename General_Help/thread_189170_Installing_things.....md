---
title: "Installing things.... ?? /"
date: 2006-06-04
forum: General Help
---

### Post by cobbweb on 2006-06-04
Hey, 
 
 I want stuff like my flash plugins for Firefox to work for every user? How do I do this? I don't like having to go to every user and installing it myself. Thanks ... 

 Cobbweb

---

### Post by aysiu on 2006-06-04
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by cobbweb on 2006-06-04
Ok, I added the repositories like the link told me to do and also went threw and installed all the flash plugins on my fathers profil (his user?) but this website

 [www.frostdevelopment.com](www.frostdevelopment.com) 

 only works on my user, but I can't get it to work when he logs in... Not sure whats up. I really need to get it to work for him, as im trying to convince him that using linux is much easier than buying ani virus software and paying threw the nose for windows. 

 Mahalo, 

 Cobbweb

---

### Post by aysiu on 2006-06-04
[QUOTE=cobbweb]Ok, I added the repositories like the link told me to do and also went threw and installed all the flash plugins on my fathers profil (his user?)[/QUOTE] I don't know what you mean about installing Flash for a particular user's profile.

If you followed the instructions in the second link, Flash gets installed for all users: ```
sudo apt-get install flashplugin-nonfree
sudo update-flashplugin
```

---

### Post by cobbweb on 2006-06-04
Ya thats the thing, It doesn't work for my fathers profile. I cant figure that one out. It works for me, does he have to have sudo privilages for it to work on his profile??? 

 Cobbweb

---

### Post by aysiu on 2006-06-04
He shouldn't, but I don't have a second user right now, so I can't test this for sure. Maybe someone else (more knowledgeable than I) will chime in on this.

---

