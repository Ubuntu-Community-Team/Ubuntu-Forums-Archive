---
title: "Unable to login after changing /etc/environment"
date: 2011-03-01
forum: General Help
---

### Post by beeyarkay on 2011-03-01
I am on 10.10 32 bit that is used as a VMWare image on my windows machine. I use that primarily for development.

I changed my /etc/environment file and looks like I messed up that and after that the VM does not allow me to login. I get to the login prompt, when I type in my password, it looks as though it is going to loing, but looks like it is restarting and it puts me back on the same login screen again.

Please help me getting this resolved.

Thanks,
Ramesh

---

### Post by tankmil on 2011-03-03
I am experiencing the same problem. Any help would be appreciated.

---

### Post by bkiran on 2011-08-09
I had a similar problem. It was not a VMWare image at least. I messed up the environemt file and i was unable to login to the desktop. I used the usb installer that i had used earlier to install, then used used sudo to change the environemt file back to its original shape and restarted. I was able to log back in after that. 
-cheers

---

### Post by fdrake on 2011-08-09
try this:
```
sudo su
cat > /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

and see if you can login now

---

