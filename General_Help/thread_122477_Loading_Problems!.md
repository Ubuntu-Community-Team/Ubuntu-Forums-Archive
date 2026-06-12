---
title: "Loading Problems!"
date: 2006-01-27
forum: General Help
---

### Post by pianoboy3333 on 2006-01-27
I've been using ubuntu for a couple months now and its been fine, now I'm having some loading issues:

ubuntu boots until the part: checking root filesystem
It then shows me the shell and prints:
> 
/: UNEXPECTED INCONSISTENCY; TUN fsck MANUALLY

[[COLOR="Red"]fail[/COLOR]]
                                                                 
[COLOR="Red"]*[/COLOR] fsck failed. Please repair manually and reboot. please note
[COLOR="Red"]*[/COLOR] that the root filesystem is currently mounted read-only. To
[COLOR="Red"]*[/COLOR] remount it read-write:

[COLOR="Red"]*[/COLOR]                 # mount -n -o remount,rw /

[COLOR="Red"]*[/COLOR] CONTROL-D will exit from this shell and REBOOT the system.


Then it propts me at the bottom:

> 
Give root password for maintenance
(or type Control-D to continue):_


*The underscore is a flashing cursor*

HELP!!!```
[HTML][/HTML]
```

---

### Post by ubunturulz11 on 2006-01-27
Type your root password when your machine asks you for it then type this:

fsck /

then type:

reboot

your machine should work after doing this!

good luck

---

### Post by pianoboy3333 on 2006-01-27
I don't know what my root password is, I don't have a set one, I WAS playing with webmin files, and setting the webmin root pass where I did somecode I believe to get a password and copied it to I think a file called webmin.users.

---

### Post by pianoboy3333 on 2006-01-27
Help?

---

### Post by pianoboy3333 on 2006-01-27
Help me?

---

