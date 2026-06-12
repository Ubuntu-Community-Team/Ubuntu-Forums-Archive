---
title: "How to set up a background automatic login account to start wifi and prey"
date: 2010-12-24
forum: General Help
---

### Post by Hansmc on 2010-12-24
If I understand correctly Ubuntu does not allow a wifi connection until a user loges in. That makes it so that prey (see preyproject.com) cannot send notices until someone has logged onto Ubuntu.

So what I would like to do (but I have no clue how) is to set up a user account that automatically, in the background, logs on at start up. Then this little user login would establish any Internet connection that is possible (wifi or lan) and start the program 'prey'. This should all be totally transparent to the user that would just see the regular log in screen. Even if you do not know how to do this, let me know if you have any idea how some of it cold be done.

Thanks for your help.

---

### Post by noah++ on 2010-12-24
Ubuntu uses NetworkManager. By default, NM requires user interaction to connect to a network. But this can be changed per-network, so that the system will connect at boot time: [http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#How_can_I_make_NetworkManager_connect_to_a_network_before_I_login.3F](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#How_can_I_make_NetworkManager_connect_to_a_network_before_I_login.3F)

---

### Post by Hansmc on 2010-12-27
Thanks for the reply. I checked out the webpage, but it does not really help me do what I had in mind.

> **noah++ said:**
> Ubuntu uses NetworkManager. By default, NM requires user interaction to connect to a network. But this can be changed per-network, so that the system will connect at boot time: [http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#How_can_I_make_NetworkManager_connect_to_a_network_before_I_login.3F](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#How_can_I_make_NetworkManager_connect_to_a_network_before_I_login.3F)

---

### Post by dcstar on 2010-12-28
> **Hansmc said:**
> If I understand correctly Ubuntu does not allow a wifi connection until a user logs in.
.........

Looking at the web site I would say that you **don't **understand it correctly.

---

### Post by Hansmc on 2011-01-05
> **dcstar said:**
> Looking at the web site I would say that you **don't **understand it correctly.

The only exception being those networks that I already logged onto once, and saved, and marked as available to every one? If there is something else that I missed, would you mind enlightening me?

The above is no use to me, since it is when my computer is boot up on a network that I have never been at before that I would most likely wont to track where it is.

In fact, my preference would be that prey automatically start tracking my computer every time it is on a net work that I have never marked as safe, in other words networks that I have never or seldom been at.

Thanks for your reply.

---

