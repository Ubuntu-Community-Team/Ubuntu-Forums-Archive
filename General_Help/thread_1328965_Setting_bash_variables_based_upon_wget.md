---
title: "Setting bash variables based upon wget?"
date: 2009-11-16
forum: General Help
---

### Post by IceRayn on 2009-11-16
The title says it all. I need a way to use a wget output of ```
wget -qO - http://cfaj.freeshell.org/ipaddr.cgi
``` and I need to set the output into a variable; $ip for example, then use notify-send to do something like ```
notify-send '$ip'
``` but this won't work. I can't get the variable to be set to the output. The wget works fine, but setting the variable doesn't want to work. Can anyone help with getting this to work?

Thanks,
IceRayn

---

### Post by Bag-O-Stuff on 2009-11-16
Try it like this:

notify-send $(wget -qO - [http://cfaj.freeshell.org/ipaddr.cgi](http://cfaj.freeshell.org/ipaddr.cgi))

---

### Post by IceRayn on 2009-11-18
> **Bag-O-Stuff said:**
> Try it like this:

notify-send $(wget -qO - [http://cfaj.freeshell.org/ipaddr.cgi](http://cfaj.freeshell.org/ipaddr.cgi))

Thanks, that worked perfectly!

---

