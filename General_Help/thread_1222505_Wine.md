---
title: "Wine"
date: 2009-07-25
forum: General Help
---

### Post by nengracia on 2009-07-25
I'm currently running Jaunty on my laptop. The primary reason why I preferred Ubuntu on my laptop is its resistance to viruses; and the secondary reason is its usability and "freeness".

Unfortunately, I need to install Picasa for Linux. With this, it installs Wine automatically in order to run the application.

My question is: If I install Wine, will my system be vulnerable to viruses and other nasty things that Windows is known for?

Need a straight and honest opinion. Thanks.

---

### Post by pbotros1234 on 2009-07-25
No it won't. The reason Linux is not vulnerable to viruses is the whole permission thing : You can't really write outside your home directory without expressed permission. That should be safe for you.

---

### Post by CatKiller on 2009-07-25
> **nengracia said:**
>  My question is: If I install Wine, will my system be vulnerable to viruses and other nasty things that Windows is known for?

If you deliberately install a virus with Wine you may, in principle, corrupt your pretend Windows environment that's stored at ~/.wine. It won't permanently affect anything else, and simply deleting that folder will cause a new pretend Windows environment to be created.

It's an old experiment, but someone did try to see if they could get Windows viruses to run in Wine. [Here]("http://www.linux.com/archive/feature/42031")'s the article.

---

