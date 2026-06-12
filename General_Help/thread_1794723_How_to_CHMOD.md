---
title: "How to CHMOD?"
date: 2011-07-01
forum: General Help
---

### Post by ehime on 2011-07-01
Just curious, in my home dir I have a list of students, some have a sub directory of wordpress
some don't, when I installed wordpress for all of my students it used me (root) as the owner.
I'd like to CHOWN those users to their own username. How would I accomplish this?

**find * | grep '$NAME/wordpress' | chown -R $NAME:www-data** ???

---

### Post by collisionystm on 2011-07-01
> **ehime said:**
> Just curious, in my home dir I have a list of students, some have a sub directory of wordpress
some don't, when I installed wordpress for all of my students it used me (root) as the owner.
I'd like to CHMOD those users to their own username. How would I accomplish this?

**find * | grep '$NAME/wordpress' | chmod -R $NAME:www-data** ???


Really, you dont need to chmod. 

Just make them the owner of their folders.

sudo chown -R <studentusername> /studentswordpressdirectory

You dont want to go chmod the whole directory because you could screw up permissions for wordpress.

Just changing the owner should be sufficient.

---

### Post by nothingspecial on 2011-07-01
Well first you don't chmod a username (that's chown).

---

### Post by nothingspecial on 2011-07-01
> **collisionystm said:**
> Really, you dont need to chmod. 

Just make them the owner of their folders.

sudo chown -R <studentusername> /studentswordpressdirectory

You dont want to go chmod the whole directory because you could screw up permissions for wordpress.

Just changing the owner should be sufficient.

Beat me to it, :P

***edit, just noticed s/he was root

---

### Post by collisionystm on 2011-07-01
> **nothingspecial said:**
> Beat me to it, :P

***edit, just noticed s/he was root


lol. Yeah running as root is not a hot idea.

---

