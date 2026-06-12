---
title: "Samba Share /srv/samba/ Permissions Question"
date: 2011-10-02
forum: General Help
---

### Post by jamesisin on 2011-10-02
I am setting up some Samba shares.  As per this article I am using /srv/samba/ for the shares:

[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)

This article says something weird (to me):

"sudo chown nobody.nogroup /srv/samba/share/"

Is nobody.nogroup a real thing?  Or is that supposed to be replaced with something?

---

### Post by jamesisin on 2011-10-02
My research tells me that in fact it is a real thing.

So let me augment my question to ask if this is a good thing or if I should be aware of any risks or problems therewith associated.


Thanks.

---

### Post by jamesisin on 2011-10-02
Ok, so this article isn't working at all.  I'm gonna have to try some other method for creating my Samba shares.  Any thoughts?

---

