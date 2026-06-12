---
title: "CMD net send, from a unix?"
date: 2010-03-12
forum: General Help
---

### Post by Alseimik on 2010-03-12
Hi there.

I'm running on a bigger LAN, and the others which uses windows are using the old DOS command "Net send" (which creates that pop-up text messages) But i'm on a unix, actually an ubuntu on this one, is there a command/way to send these messages like the "net send"? even better, also receive? because "wall" doesn't really work here! I would really appreciate if  cross over was possible!

Thanks

---

### Post by iponeverything on 2010-03-12
install samba then:

smbclient -M 

google for: samba "Net send" or whatever for ideas.

---

