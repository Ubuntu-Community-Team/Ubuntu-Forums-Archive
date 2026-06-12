---
title: "User removed from user list"
date: 2009-07-17
forum: General Help
---

### Post by kogger on 2009-07-17
I'm messing around with my girlfriend's ubuntu setup in order to make it somewhat usable, and one thing I wanted to do was to mount her MacOSX partition so that the two operating systems can communicate. I read in [this topic](http://ubuntuforums.org/showthread.php?t=311476) that the best way to get easy read/write access is to set your user id in ubuntu to 501, using the command "sudo usermod -u 501 <YOUR_USERNAME>".

I did that, but for some reason now the user isn't listed. I can still log in using the same username and password, but the face browser doesn't show anything and going to System->Administration->Users and Groups only lists root.

All I did was change the user id. The account is still there, and I can log into it...but there doesn't seem to be any representation for it. Any idea how I can get it to be listed again?

---

### Post by lykwydchykyn on 2009-07-17
So that it doesn't show all your miscellaneous system accounts, GDM has a lower threshold on the UIDs it will display in the logon list.  Since ubuntu defaults to UID 1000 for the first user, I think this threshold is set to 1000 by default.

You can run "gksudo gdmsetup" and there should be a way to change this, or just add that one user manually.

---

### Post by kogger on 2009-07-17
It's always at times like this that I feel rather stupid.

Thanks. That worked. =)

EDIT: Well, it kind of worked. It's listed in the login screen, but still not in System->Administration->Users and Groups. That still only lists root.

---

### Post by kogger on 2009-07-17
Well, technically, I can list it again by going to gconf-editor and setting /apps/gnome-system-tools/users/showall to true, but then it also lists a whole bunch of other weird users that I really don't want listed, like "backup", "daemon", and "ircd."

---

### Post by lykwydchykyn on 2009-07-17
> **kogger said:**
> It's always at times like this that I feel rather stupid.


You should feel smarter.  You just learned something new! :-)
> 
EDIT: Well, it kind of worked. It's listed in the login screen, but still not in System->Administration->Users and Groups. That still only lists root.

I would assume that any tool which has to filter out system users has got to have the threshold specified somewhere.  How to find it just depends on the tool.  Not every Linux or Unix system starts at UID 1000, so this has to be configurable.

I'm not really a GNOME guy so I can't help you on that one, but you might find it by grepping through the gnome configs for the number 1000, e.g.
```

grep -iHr 1000 /etc/gnome

```

(I don't know if the configs are actually in /etc/gnome, but someone can correct me on that).

---

### Post by kogger on 2009-07-17
Nope, that didn't come up with anything. Good try, though. =P

---

### Post by sisco311 on 2009-07-17
if i understand your issue correctly, you have to set the uid/gid to be the same on both Ubuntu and Mac OS X. 

since setting the uid to 501 in Ubuntu causes inconvenience, why don't you try to set it to 1000 in Mac OS X?

---

### Post by kogger on 2009-07-17
That's also a possibility, and I'll look into it.

---

