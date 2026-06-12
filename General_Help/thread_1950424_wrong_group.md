---
title: "wrong group?"
date: 2012-03-31
forum: General Help
---

### Post by conradin on 2012-03-31
Hi all,
I have a user account on a friends computer, but the permissions are screwy.
I can use sudo commands. every time I log in via ssh, I get a message stating:
cannot find name for group ID 501

I have no idea what that means...
but when I view the other users of the home directory, I see the suspicious 501. 
```
$ll
drwxr-xr-x  6 ilaforge     ilaforge     4096 2012-03-29 12:18 ilaforge
drwxr-xr-x  5 jreistad     jreistad     4096 2012-03-30 11:52 jreistad
drwxr-xr-x 16 conradin              501 4096 2012-03-31 19:17 conradin


```
I just want my home directory to function normally so I can put my web pages up. is 501 a group or a folder? what is ll telling me here?

---

### Post by HiImTye on 2012-03-31
501 is the GID there, you can chown it to the user and their group using
```
sudo chown -R user:group folder
```
generally, user groups start at 1000, unless whoever made them creates them differently

---

### Post by Dangertux on 2012-03-31
> **HiImTye said:**
> 501 is the GID there, you can chown it to the user and their group using
```
sudo chown -R user:group folder
```generally, user groups start at 1000, unless whoever made them creates them differently

Note : RHEL based systems usually start at 500.

The above posted solution should work for you but if you want to find out what group that is you can try

```

getent group 501

```

Hope this helps.

---

### Post by HiImTye on 2012-03-31
true but since it has an [Ubuntu] prefix I hadn't considered Red Hat problems

---

### Post by Dangertux on 2012-03-31
I was just pointing it out, newer RHEL releases have changed to the 1000 starting point.

---

### Post by HiImTye on 2012-03-31
I did not know that :D

---

