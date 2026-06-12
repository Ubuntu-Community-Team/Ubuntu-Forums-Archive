---
title: "Firefox does not show pictures."
date: 2012-04-04
forum: General Help
---

### Post by emptycoder on 2012-04-04
Hello everyone, I'm facing a strange problem with Firefox, When I search for images they don't load, the page takes forever with nothing appears (See Screenshot) after refreshing it might work and some times it doesn't, and I'm having the same thing with DeviantArt.
I searched around and some said (Load Images Automatically) might not be checked on Firefox - Preference -  Content, I checked out and it was checked, Am I missing something here?
Thanks.

[[IMG]http://img821.imageshack.us/img821/9/screenshotat20120404230.th.png[/IMG]]("http://imageshack.us/photo/my-images/821/screenshotat20120404230.png/")

---

### Post by kc1di on 2012-04-04
what addons do you have enabled?
try turning them all off and adding them back one at a time see if one of them affect the performance on loading images. 
FF is working fine here.

---

### Post by emptycoder on 2012-04-04
I tried it and nothing changes, any more ideas?

---

### Post by kc1di on 2012-04-04
which version of ubuntu you using? which version of FF?
are all pages slow?  do you have any firewall set up ? 

I'm just full of questions huh :)

---

### Post by hughr2005 on 2012-04-04
Have you ruled out a network issue? Could it be a max-filesize setting on your router?

---

### Post by emptycoder on 2012-04-04
I use latest editions, Ubuntu 11.10 and Firefox 11.
I have discovered something strange, when I set Firefox to use some proxy it works normal but when I switch back the problem occurs again.

---

### Post by lovinglinux on 2012-04-05
> **emptycoder said:**
> I use latest editions, Ubuntu 11.10 and Firefox 11.
I have discovered something strange, when I set Firefox to use some proxy it works normal but when I switch back the problem occurs again.

Probably a DNS issue. Try OpenDNS or Google DNS.

---

### Post by emptycoder on 2012-04-05
OpenDNS somehow fixed the problem, thanks a lot.

---

