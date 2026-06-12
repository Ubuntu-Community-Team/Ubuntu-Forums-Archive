---
title: "Accessing Windows Domain Shares fro, 12.04 64bit"
date: 2012-05-08
forum: General Help
---

### Post by SnakesAlive on 2012-05-08
Hi,

I am a newbie and this is my first post so high!

I have a newly installed client which is working great so far. However, when i try and access any windows shares i continuously get prompted for my credentials and they dont open. I can ping to and from the devices, and resolve all the names and the domain.local from the ubuntu machine. The credentials are 100% ok for those shares. This is the case whether i goto Network - browse Network or whether i file connect to server.

Any ideas?

---

### Post by SnakesAlive on 2012-05-09
Anyone help?

---

### Post by SnakesAlive on 2012-05-11
2 days, 120 views yet no suggestions!

---

### Post by The Cog on 2012-05-11
I just hit a problem like that this morning. It turned out that I now have to enter the domain name in upper case - in previous versions, both upper and lower case worked.

This was using gigolo in Xubuntu to create the connection, so I don't know if this change might affect you.

---

### Post by SnakesAlive on 2012-05-11
> **The Cog said:**
> I just hit a problem like that this morning. It turned out that I now have to enter the domain name in upper case - in previous versions, both upper and lower case worked.

This was using gigolo in Xubuntu to create the connection, so I don't know if this change might affect you.

Thank you! As soon as i tap in the credentials in Capitals it connects fine. Thank you very much!

---

### Post by The Cog on 2012-05-11
Glad to hear that worked. I guess this will be catching a lot of people out.

You can mark the thread solved by using the **[COLOR="Red"]_Thread Tools_[/COLOR]** menu at the top of the page.

---

