---
title: "Keyring Duplicate Problem"
date: 2011-03-12
forum: General Help
---

### Post by Gael33 on 2011-03-12
I am using Ubuntu 10.10 (Maverick) X86 with a Netgear Wireless Connection and whenever I boot up I receive Two password keyring notifications to get on line. Is there a way of removing one of the duplicated notifications, because as soon as I enter my password into the first notification and press enter, I am on line. The second notification appears to do nothing. 

Thanks.

---

### Post by tredegar on 2011-03-12
> I receive Two password keyring notifications to get on line. Is there a way of removing one of the duplicated notifications,

Ubuntu's "keyrings" drive me mad. My LAN is properly secured.

My solution was to delete everything in **~/.gnome2/keyrings/**

Then, when it asked for a keyring thing, I left it all blank & clicked OK.
I accepted "Unsafe" storage.

It works for me. YMMV.

---

### Post by Gael33 on 2011-03-13
> **tredegar said:**
> Ubuntu's "keyrings" drive me mad. My LAN is properly secured.

My solution was to delete everything in **~/.gnome2/keyrings/**

Then, when it asked for a keyring thing, I left it all blank & clicked OK.
I accepted "Unsafe" storage.

It works for me. YMMV.

Thank you, I have done the same and now the problem is solved. :D

---

