---
title: "A rkhunter message is annoying me.  Some advice needed."
date: 2006-02-28
forum: General Help
---

### Post by Mustard on 2006-02-28
I've got rkhunter running regular checks for rootkits, and I'm getting this message from rkhunter..(in particular the reference to **gnokiid.swp**)

```
To: root@localhost.localdomain
Subject: [rkhunter] Daily run
From: root <root@localhost.localdomain>

Line:
  [ Warning! ]
-----------------------------------------------------------------

Found warnings:
[06:50:53] WARNING, found:  /dev/.static (directory)  /dev/.udevdb (directory)
+/usr/sbin/.gnokiid.swp (data)

-----------------------------------------------------------------

If you're unsure about the results above, please contact the author of
Rootkit Hunter. Fill in contact form: http://www.rootkit.nl/contact/
Some errors has been found while checking. Please perform a manual check on this
```

Now I installed gnokii while I was mucking around trying to hook up a mobile phone via usb to linux.  The experiment was a total failure, and I have since uninstalled gnokii.  Rkhunter is picking up this file as some type of sign of a rootkit.  I can live with the fact that its a 'false positive', but I am curious as to whether I can just delete this file now that gnokii is uninstalled.  Any advice?

I have no idea what the other two warning are for, but I've had them since the first day I installed rkhunter.

---

### Post by Mustard on 2006-03-01
*bump*

:)

---

