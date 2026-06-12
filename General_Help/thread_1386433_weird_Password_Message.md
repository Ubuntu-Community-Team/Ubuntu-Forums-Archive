---
title: "weird Password Message"
date: 2010-01-20
forum: General Help
---

### Post by AFUNA on 2010-01-20
Am trying to open empathy (and many other programs)
and I face a weird window asking me for password with two buttons (Ok - Deny)
and when I add root's password it doesnt accept it ..
How can I solve this problem ?
pic of the problem attached ;)

---

### Post by ks07 on 2010-01-20
> **AFUNA said:**
> Am trying to open empathy (and many other programs)
and I face a weird window asking me for password with two buttons (Ok - Deny)
and when I add root's password it doesnt accept it ..
How can I solve this problem ?
pic of the problem attached ;)
The password it wants is your password not root's (who shouldn't have a password in the first place unless you've changed something).

---

### Post by AFUNA on 2010-01-20
> **ks07 said:**
> The password it wants is your password not root's (who shouldn't have a password in the first place unless you've changed something).
I didnt change anything and still work with sudo original password fine.. so how can I remove it ?

---

### Post by ks07 on 2010-01-20
> **AFUNA said:**
> I didnt change anything and still work with sudo original password fine.. so how can I remove it ?
Sorry but I dont know enough about the issue to solve it :(. However, a quick google search for default keyring unlocked returned many results which may have answers for you. Otherwise, hopefully someone enlightened will be along soon to help. ;)

---

### Post by AFUNA on 2010-01-20
Thanks alot Ks07 for being concered enough to reply me :)
I will try my luck with google results and get back here if I failed to solve the problem.

---

### Post by Jackzor on 2010-01-20
What is listed under```
 /home/(yourname)/.gnome2/keyrings
```?

---

### Post by AFUNA on 2010-01-20
> **Jackzor said:**
> What is listed under```
 /home/(yourname)/.gnome2/keyrings
```?
I dont think that there is a folder or a file with the name .gnome2 in the home folder
After I opened /home/(myname)/ I couldnt find any folder with the name  .gnome2
I even tried to search for it, Unfortunately didnt find any folder or file with this name :(

---

### Post by synapsys on 2010-01-20
It's hidden.

Right click -- view hidden files

---

### Post by AFUNA on 2010-01-20
Thanks problem solved by deleting it from its root.
knew where to try from this post
[http://ubuntuforums.org/showthread.php?p=7733950#post7733950](http://ubuntuforums.org/showthread.php?p=7733950#post7733950)
As Ks07 said little google will solve it but I didnt knwo the problem name to solve it

Thanks guys for helping me out ;)

---

