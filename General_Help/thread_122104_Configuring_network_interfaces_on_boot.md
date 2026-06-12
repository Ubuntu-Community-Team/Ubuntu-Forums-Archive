---
title: "Configuring network interfaces on boot"
date: 2006-01-26
forum: General Help
---

### Post by era86 on 2006-01-26
When I boot up my computer and it hits the ubuntu splash screen, it takes a long time for the Configuring network interfaces... setting to complete. Is there a way to shorten the timeout rate on this?

Thanks

-ERA

---

### Post by Sparkalo on 2006-01-26
I have the same problem, but rather than spending time trying to resolve it, I just press ctrl+c when I get to the network configuration part to skip it : P.  It doesn't affect my access because GTKwifi configures everything on startup.  Try ctrl+c to skip and see if it works for you.  

Another thing you can try is editing your /etc/network/interfaces file to manually configure your crap, I'd give you more information as to whether or not this would actually help, but I have no idea what kind of an interface your using nor why exactly it's taking so long (my guess is wireless + encryption)

Good luck and Stay Frosty!

---

### Post by ned.b on 2006-01-27
check my post here for a fix:

[http://www.ubuntuforums.org/showthread.php?t=115239&page=3](http://www.ubuntuforums.org/showthread.php?t=115239&page=3)

---

