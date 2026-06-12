---
title: "Deleted Admin Group"
date: 2011-06-20
forum: General Help
---

### Post by aruhela on 2011-06-20
Unknowingly I have deleted admin group? Now, Will it be sufficient to create admin group with command "addgroup admin"? How should I restore related setting of admin user?

---

### Post by idoitprone on 2011-06-20
```
sudo groupadd admin
```I forgot ubuntu defaults. Just return it to its orginal state.


adding users to a existing group
```
usermod  -a -G admin  user
```[http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/](http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)

---

### Post by linkageless on 2011-06-20
I would find the GID of the former admin group, perhaps by looking at a file that you know to be group owned by admin. I'd use that to manually re-create the admin group in the /etc/group file. (on my system, admin GID is 114, but I don't know of any files that use it, yours may be different.)

Once you have admin group back, add any users that should be there. (I have just my normal login username.)

Here's a snippet from my /etc/group file:
> 
netdev:x:113:
admin:x:114:linkage
polkituser:x:115:

---

### Post by collisionystm on 2011-06-20
> **idoitprone said:**
> ```
sudo groupadd admin
```I forgot ubuntu defaults. Just return it to its orginal state.


adding users to a existing group
```
usermod -a -G admin user
```
[http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/](http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)


```
usermod -G <group> -a <user>
```

---

### Post by idoitprone on 2011-06-20
that works too

---

### Post by aruhela on 2011-06-20
> **idoitprone said:**
> that works too

How do i know which files are created/owned by Admin group previously? Can you tell me a few files?

---

### Post by idoitprone on 2011-06-20
it does really matter, since those files are owned by admin. It will only be a problem if those files uses a gid and uid.

Try restore it to defaults.


```
sudo groupadd admin -g gid
```

example 

```
sudo groupadd tacosauce -g 8008
```


finding files 
```
find / -group admin
```

---

### Post by aruhela on 2011-06-20
I executed following command with root privileges but I couldn't get even a single file.
[CENTER]find / -group admin
[LEFT]
How should i proceed next?
[/LEFT]
[/CENTER]

---

### Post by idoitprone on 2011-06-20
yep if permission denied add sudo


```
sudo find / -group admin

```

---

### Post by linkageless on 2011-06-21
Having thought about this, I don't ever remember seeing a file with group ownership of admin (and indeed haven't been able to find one). I'm not saying that hasn't been used for any file ownership at some point, but I think I've remembered why it exists in Ubuntu...

To quote from the /etc/sudoers file:
"# Members of the admin group may gain root privileges"

So you'll probably be fine re-adding the group with whatever GID. I'd put your user(s) back into the group while you're at it.

This all assumes that you have been able to get in as root without this sudo rule working! Good luck!

---

### Post by linkageless on 2011-06-21
> **idoitprone said:**
> yep if permission denied add sudo


```
sudo find / -group admin

```

Sadly this won't work if the admin group has been deleted, you'd need to search on GID, which is what we would want to find!

If restoring the original GID is important to you, a clue could be had from looking at the /etc/group file for a missing number in the sequence before your first users group. On the system I'm using, admin is 114, just after netdev which is 113.

---

