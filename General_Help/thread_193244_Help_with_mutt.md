---
title: "Help with mutt"
date: 2006-06-09
forum: General Help
---

### Post by jsmidt on 2006-06-09
Somebody sent me a pdf as an attachment. I know in mutt if I push "v" I see the attachment but how do I view it in a pdf viewer like xpdf? Thanks.

---

### Post by croak77 on 2006-06-09
[QUOTE=jsmidt]Somebody sent me a pdf as an attachment. I know in mutt if I push "v" I see the attachment but how do I view it in a pdf viewer like xpdf? Thanks.[/QUOTE]

It's been a while since I've used mutt. Unless things have changed, then you need to specify it in your mailcap.

Edit your .muttrc And add:
set mailcap_path="~/.mailcap" 
Or wherever you want it to be.
 
Edit ~/.mailcap. Add: 
application/pdf;                     xpdf %s

Check out Gary Johnson's Mutt Page too. He's has some cool scripts.
[http://www.spocom.com/users/gjohnson/mutt/](http://www.spocom.com/users/gjohnson/mutt/)

Here the Mutt manual:
[http://www.mutt.org/doc/manual/manual-5.html](http://www.mutt.org/doc/manual/manual-5.html)

---

