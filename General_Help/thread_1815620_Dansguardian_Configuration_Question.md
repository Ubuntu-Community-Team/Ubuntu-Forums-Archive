---
title: "Dansguardian Configuration Question"
date: 2011-07-31
forum: General Help
---

### Post by matthew.c.tx on 2011-07-31
Quick question:

I'm setting up a public kiosk for my shop so people can only browse our website. However, I don't want them to be able to go to our shopping cart (buying is something they need to do on a private computer).

1. Blanket ban in DG using ** in the banned sites list. Worked great.
2. Put my website in exception site list. (Perfect, DG is awesome)
3. Put "mywebsite.com/cart" in banned URL list. Didn't do anything.

I get that exception overrides banned, but is there anything that is above exceptions? How would one go about doing this?

(If it helps, the kiosk is running Lubuntu with Firefox in rkiosk mode. Our proxy uses DG + Squid.)

Thanks.

---

### Post by psrdotcom on 2011-09-16
Have you tried regular expressions in dansguradian?

---

