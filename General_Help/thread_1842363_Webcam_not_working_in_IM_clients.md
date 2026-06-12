---
title: "Webcam not working in IM clients"
date: 2011-09-11
forum: General Help
---

### Post by LackadaisicalLove on 2011-09-11
I am using a Sony VAIO VPCEA3S1E laptop with Natty, and I just can't get any IM clients to send or receive webcam invites through msn.

The webcam itself is working fine, Cheese fires up and snaps away a treat, but sending via amsn, emesene, Pidgin and Empathy seems to be something that is proving difficult.

I have seen a few people with similar problems, but usually just with one client, or it becomes resolved when Ubuntu's firewall is disabled.
I have tried this, and nothing works.

My boyfriend's brother told me it was a port problem, but I'm not too sure as he tends to talk out of his rear end sometimes. If he is right though, what would I have to do to solve this issue?

---

### Post by no2498 on 2011-09-12
see if this helps
open a terminal copy/paste

 LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so Empathy 
click enter
you can put any name behind that just take off the Empathy 
and you may need flash installed

---

### Post by LackadaisicalLove on 2011-09-13
No luck at all =/
And I have flash.

---

### Post by no2498 on 2011-09-13
? did empathy open at all
you may need not to use the caps

---

### Post by LackadaisicalLove on 2011-09-14
Sorry it took a while to reply, been away for a bit.
I did it with amsn, and it did open. Contacts were still not receiving webcam invites though.

---

### Post by no2498 on 2011-09-15
sorry but i dont know how to fix the invites

---

### Post by no2498 on 2011-09-15
was just thinking do you allow popups in your browser

---

### Post by LackadaisicalLove on 2011-09-16
It blocks popups, but has a toast to click on to open them if I need to?

---

### Post by no2498 on 2011-09-16
set it to allow popups and cookies
see if that helps

---

### Post by no2498 on 2011-09-16
something i just started seeing is 
skype or cheese may be set to auto startup after a restart
some web cam program any way
they need to be turned off 
and do a restart
it could also be adobe flash

---

