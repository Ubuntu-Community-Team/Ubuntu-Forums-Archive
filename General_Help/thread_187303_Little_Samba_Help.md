---
title: "Little Samba Help?"
date: 2006-06-02
forum: General Help
---

### Post by dmorel on 2006-06-02
I have a directory I want to make available to other devices (XBOX media center  and my son's XP machine) on the local LAN.

I have edited smb.conf to include:

```


[Media]
path = /media/Media
available = yes
browseable = yes
public = yes
writable = yes
guest ok = yes

```

and restarted samba.
However, this does not appear to actually enable guest access to the share, because XP continues to receive a username/password prompt.

I presume that somewhere in the smb.conf file (which I have read from end to end three times) there is something that I need to do in order to enable guest access at a global level before the actual share I've created can be reached.
Can anyone tell me what that may be?

thanks,
-morel

---

### Post by linuchsan on 2006-06-02
is the workgroup the same on all computers?

---

### Post by dmorel on 2006-06-02
yeah, it is...
thanks!

---

### Post by givré on 2006-06-02
What i did is setting up security to share
```
# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
   security = share

```
And set myself to guest account
```

guest account = flo
invalid users = root

```
Hope that will help

---

### Post by linuchsan on 2006-06-02
and you did setup a unix user for the guest account?

---

### Post by dmorel on 2006-06-02
[QUOTE=givré]...
Hope that will help[/QUOTE]


Why yes, yes it will....

that did the trick, many thanks!

-morel

---

### Post by rbgCODE on 2006-06-09
Maybe one of you guys can help me?  I am running xbox with centOS on it, and I had created smb shares. Now from XP i can access it, \\xShare\ from both of my xboxs I can access it, but when I open ubuntu networks up it doesnt show it, and it wont even let me ping the IP.  Any ideas?

---

