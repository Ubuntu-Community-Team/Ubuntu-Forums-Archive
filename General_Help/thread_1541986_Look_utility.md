---
title: "Look utility"
date: 2010-07-29
forum: General Help
---

### Post by podianu on 2010-07-29
Maybe a mundane question. I would like to use the look utility to use the wbritish dictionary without having to give the path each time, how do I set it to default to this. The default path is /usr/share/dict/words. I have downloaded the wbritish list as well.
  Thanks

---

### Post by samijam on 2010-07-29
for me /usr/share/dict/words is a symbolic link to /etc/dictionaries-common/words which is itself a symbolic link to /usr/share/dict/american-english

So, assuming yours is the same, delete the /etc/dictionaries-common/words link and then:

ln -s /path/to/your/wbritish /etc/dictionaries-common/words

---

### Post by podianu on 2010-08-02
Thanks your info was helpful, unfortunately deleted /etc/dictionaries-common/words file itstead instead of the link; my mistake. How do I recover?

---

### Post by lyall on 2010-08-02
check your trash can first
it should be there if you have not cleaned your trash can
if it is still there replace it using the restore

good luck and have fun learning

---

### Post by podianu on 2010-08-03
I have used sudo to rm the file. Does the root account have a separate trash can for the restore. Can one log in using su and access the trashed files? Especially after powering off the PC?

---

### Post by podianu on 2010-08-03
Hi guys
 Located the sudo -s command became root, searched trash; no record of file deleted. Looks like I will have to reload the dictionaries commom package again. Will that do the trick? I wonder? But then there are a number of programmes dependant on it.

---

### Post by podianu on 2010-08-03
No need to reinstall, I copied the wbritish list to a fresh words file in /usr/share/dict, no need to link either, question is why link at all? Anyway problem solved; look utility uses the wbritish file! Thanks, I consider the matter resolved.

---

