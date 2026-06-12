---
title: "online storage that I can SSH into"
date: 2010-05-17
forum: General Help
---

### Post by the pearly gates on 2010-05-17
Hello,

Does anyone know of a service that would allow me to have data files (and also webpages) stored online that would be accessible via SSH? 

I've heard of sites like mozy.com, but they want me to download some program to connect to their servers, and I would prefer to be able to just SSH in.

Basically, I want to have access to my_username@some_ip_address in SSH.  Do you know of a service like this? If not, do you know what might a service like this be called that I could search online for?

Thanks,

---

### Post by SlidingHorn on 2010-05-17
Most hosts will allow you SSH access if you have a VPS account.  I have one at 1&1 and I'm pretty happy with their services overall.  all you do to access it is:

```
ssh <user>@<address>
```

When prompted, enter your password and be on your way...

---

