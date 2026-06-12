---
title: "how to use apt-cacher with the mini iso?"
date: 2011-03-20
forum: General Help
---

### Post by markp1989 on 2011-03-20
i have just set up apt-cacher  my file server to speed up package installs (and to reduce bandwidth use) 

Im wondering if it is possible to use the apt-cacher with the mini iso, so each machine doesn't have to redownload the packages from the net?

Thanks for reading, Mark

---

### Post by Wobblybob on 2011-03-21
Hi mate, does my post here [[COLOR="Navy"]http://myubuntublog.wordpress.com/2009/05/17/an-apt-server-using-apt-cacher/[/COLOR]]("http://myubuntublog.wordpress.com/2009/05/17/an-apt-server-using-apt-cacher/") help?

---

### Post by markp1989 on 2011-03-21
> **Wobblybob said:**
> Hi mate, does my post here [[COLOR="Navy"]http://myubuntublog.wordpress.com/2009/05/17/an-apt-server-using-apt-cacher/[/COLOR]]("http://myubuntublog.wordpress.com/2009/05/17/an-apt-server-using-apt-cacher/") help?

hey, thanks for replying to me :) 

whilst you blog is an interesting read, I have already setup apt-cacher on my fileserver  (although I'm gonna move the cache from the root drive in a sec as you described)

I would like to be able to  use my local apt-cacher when installing from the minimal ISO

---

### Post by Wobblybob on 2011-03-22
> **markp1989 said:**
> hey, thanks for replying to me :) 

I would like to be able to  use my local apt-cacher when installing from the minimal ISO

sorry mate missed the point there, as the mini iso install pulls in packages over the net as it installs[if i remember correctly] I'm not sure how/if you could do that. It would be a neat trick if you could achieve it though, I hope someone can help you with it..

P.S
I may be way off base but does the mini.iso image use the text based installer which asks lots more questions than the gui version? If so does it not ask for a proxy at some point and if so you could point it to a networked PC with your apt cache on it as in [http://my_apt_server:3142](http://my_apt_server:3142).

If you try it and get it to work please post back as it would be worth trying in the future.

Good Luck

---

### Post by markp1989 on 2011-03-22
just got it working which I verified by watching the access logs of apt-cacher 

on the mirror I selected the default one, then I entered my the details of my apt-cacher on the http proxy screen (dont know why I didnt think of that before!!) 

right now its doing the install (in a virtual machine), still watching the apt-cacher logs.

so come release day, the packages only need to be downloaded once for the 4 or 5 machines I will be installing it on.

---

### Post by Wobblybob on 2011-03-23
Good to know, I've been thinking of doing a minimal install of Ubuntu then adding the xfce desktop so I might well give this a try after Natty is released.

If all went well you could mark this thread as solved now.

---

### Post by markp1989 on 2011-03-23
> **Wobblybob said:**
> Good to know, I've been thinking of doing a minimal install of Ubuntu then adding the xfce desktop so I might well give this a try after Natty is released.

If all went well you could mark this thread as solved now.

thanks, it appears to work in a virtual machine,  gonna see if i can find a real pc spare, cant see why it would be any different, but just to make sure

---

