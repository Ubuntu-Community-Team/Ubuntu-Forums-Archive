---
title: "Black screen post GRUB2, login and pword ok. Then nothing"
date: 2011-05-15
forum: General Help
---

### Post by sea_dawg on 2011-05-15
When restarting my dual boot system I wanted to start Win XP.  Scrolling down the list I think I hit the left arrow key by mistake.

I got what I think is the recovery menu.  I chose #1, Continue Normal Boot (at least that's what I think it was).

Then I was prompted for my login and password.  The system accepted those and seemed happy but will go no further.  

I've tried entering 'exit'.  This simply causes the system to ask for login and pword again.

Please see the attachment of my screen.

I've searched the forum and haven't found a similar situation with a solution.

I am reluctant to pull the power to shut down.  

Any advice on what to do next?

Until this my system has been very stable and reliable.

Thank you.

Ubuntu 10.10
Gateway 507 GR,  Pentium IV,  4 GiB RAM
Dual boot Ubuntu 10.10 / Win XP
Ubuntu is on it's own HDD

---

### Post by MAFoElffen on 2011-05-15
> **sea_dawg said:**
> When restarting my dual boot system I wanted to start Win XP.  Scrolling down the list I think I hit the left arrow key by mistake.

I got what I think is the recovery menu.  I chose #1, Continue Normal Boot (at least that's what I think it was).

Then I was prompted for my login and password.  The system accepted those and seemed happy but will go no further.  

I've tried entering 'exit'.  This simply causes the system to ask for login and pword again.

Please see the attachment of my screen.

I've searched the forum and haven't found a similar situation with a solution.

I am reluctant to pull the power to shut down.  

Any advice on what to do next?

Until this my system has been very stable and reliable.

Thank you.

Ubuntu 10.10
Gateway 507 GR,  Pentium IV,  4 GiB RAM
Dual boot Ubuntu 10.10 / Win XP
Ubuntu is on it's own HDD
After login, enter 
```

sudo shutdown -r now
# OR #
sudo reboot

```Either command will shutdown all running services, cleanly exit the file systems and reboot the system.. That will get you back into familiar territory.

---

### Post by sea_dawg on 2011-05-15
Update:

I seem to have a running system without Gnome.  Please see the attachment after the top command.

Does anyone know a way to get Gnome running from here?  Or safely shutdown my system?

Thanks

---

### Post by sea_dawg on 2011-05-15
MAFoElffen,

Thank you.  Your code indeed worked!  I'm posting this from the problem system.

Dunno what happened between you answer to my first post and my update.  For some reason your post didn't show.

No matter.  Thank you!  I'm up and running again.

---

