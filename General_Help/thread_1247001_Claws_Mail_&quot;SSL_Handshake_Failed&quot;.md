---
title: "Claws Mail &quot;SSL Handshake Failed&quot;"
date: 2009-08-22
forum: General Help
---

### Post by r11_kaede on 2009-08-22
Hey guys,

I'm currently using Claws 3.7.2 from the ppa for Hardy. (I'm using Hardy atm). Whenever I try to send mail via smtp, i will always get the "SSL handshake failed" error. However, this problem only comes along when i try to SEND mail. Receiving via imap/pop works perfectly fine.

Any help/tips would be greatly appreciated.

Thanks :)

---

### Post by ckunzler on 2010-01-04
I believe I was having the same problem.  First thing I did was in account preferences> ssl > send (SMPT): check don't use SSL.  That worked.

But I wanted to use SSL so reversed what I did above (So if you want to use SSL don't make that change) and went to advanced settings and changed the SMPT port to 465 (because I'm configuring gmail and that's what they said I should use for SSL [http://mail.google.com/support/bin/answer.py?hl=en&answer=13287]("http://mail.google.com/support/bin/answer.py?hl=en&answer=13287") )

I hope that was clear.  Normally I'm looking for answers not giving them.

---

