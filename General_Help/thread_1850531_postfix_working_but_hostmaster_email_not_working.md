---
title: "postfix working but hostmaster email not working"
date: 2011-09-26
forum: General Help
---

### Post by jerry01 on 2011-09-26
hi,
i'm at my wits' end.

i have postfix running but somehow [email]hostmaster@*mysite*.com[/email] gets redirected to root@mail, and the email crashes.  i need to have [email]hostmaster@mysite.com[/email] working.  

can someone tell me how i can either turn off the aliasing for hostmaster, or how i can get the root@mail to work. i'm not sure i'm making myself entirely clear.  basically i seem to get neither hostmaster or root emails to work. i can get other email addresses to working, but not these two.

cheers

---

### Post by jerry01 on 2011-09-27
ok i've got it working now.

i had the wrong data in myorigin file 

sorted

---

