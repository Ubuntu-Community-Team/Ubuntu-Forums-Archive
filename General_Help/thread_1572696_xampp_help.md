---
title: "xampp help"
date: 2010-09-11
forum: General Help
---

### Post by Crizzie on 2010-09-11
Hi,

I'm pretty new at using xampp and I'm having trouble setting everything to my liking. I've followed this install guide ( [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html) ) and everything appears to be working correctly. However, I'm finding it rather difficult to be able to create documents and use the htdocs with ease. 

Is there a way to move the entire htdocs to like my home directory or something? I'm not worried with security as this is only setup for localhost and I'm behind a router regardless. I'd just like to have my htdocs located at /home/chris/htdocs/ instead of where it's at now /opt/lampp/htdocs

---

### Post by Crizzie on 2010-09-11
Anyone?

---

### Post by Crizzie on 2010-09-11
Is this even the correct section to post this in?

---

### Post by v1ad on 2010-09-11
just copy and paste it over instead of moving, thing is with that you would have to change all the files that use that config to that directory. personally i never use xamp, i would just install lamp, and the htdocs you really don't modify them everyday. modify em and leave em. but its your choice.

---

### Post by Crizzie on 2010-09-11
> **v1ad said:**
> just copy and paste it over instead of moving, thing is with that you would have to change all the files that use that config to that directory. personally i never use xamp, i would just install lamp, and the htdocs you really don't modify them everyday. modify em and leave em. but its your choice.

I don't understand what you mean by copy and paste it over instead of moving. I understand that I could create the directory there, but where in the configuration do I set that up?

I'm not entirely sure, but I believe xampp and lampp is the same software except xampp is the newer updated name. I think they just left all of the directories and everything on linux as lampp so people didn't get confused. Again, I'm not completely sure on this.

I would be modifying the htdocs on a daily basis. I would actually be in there quite often modifying, adding, and removing files. With the default install the htdocs has a lock on it and I'm not able to add documents or create new documents unless I'm running as root I believe. I understand this is for a security purpose, but since this is only a local server I shouldn't have to go through all this trouble.

---

### Post by v1ad on 2010-09-11
if you copy and paste you can work on the conf files with a backup plan if something goes wrong. 

o i see what your issue is. you see if you installed through apt-get you can get it kept updated, but since you went that way you can just chown it.

chown -R username /opt/lamp 

and it will take care of that
also if you want to have a username for it i would make a separate one name web or something.

useradd -b /opt/lampp web

then chown that user.
basically u add a user with the home directory in a different spot. and maybe just copy .bashrc and .profile from your username to /opt/lampp and chown after that.

---

