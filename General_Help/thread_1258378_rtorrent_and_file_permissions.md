---
title: "rtorrent and file permissions"
date: 2009-09-04
forum: General Help
---

### Post by koushiro on 2009-09-04
hi guys, newbie here

I want to know if it's possible to set the default permission of a folder to 766 so that any subsequent files added also gets to inherit its permissions. Or if not, is there anyway for rtorrent to set these permissions after moving them to a specified folder?

thanks

---

### Post by Ahmedmb on 2009-09-20
:)
Any News i need that also
:)

---

### Post by moyam01 on 2009-09-20
chmod -r 766 [filename]



It should be fine after that. rtorrent (at least for me) sets the permissions according to the user that it is in. Also, if you are not using an rtorrent config file, you might want to take a look at that.

---

