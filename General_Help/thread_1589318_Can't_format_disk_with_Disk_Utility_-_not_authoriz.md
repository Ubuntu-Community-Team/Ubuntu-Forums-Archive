---
title: "Can't format disk with Disk Utility - not authorized"
date: 2010-10-06
forum: General Help
---

### Post by rjmarshall on 2010-10-06
Hi,

I apologize if this has been covered elsewhere, I did a search but wasn't able to find it...

I'm new to Ubuntu 10.04 and I'm trying to format a disk with Disk Utility but I get "not authorized". I haven't figured out how to run the utility from the menu with privileges. I assume (may be a bad assumption) that there must be some way to elevate my privileges (I'm the only user on this system) temporarily so that all of the applications from the menu will run as root, but I haven't found it. Is there a way to do that? Or is there a way to run an individual application from the menu and get prompted for the password?

Thanks,

Rob

---

### Post by TeoBigusGeekus on 2010-10-06
Try with gparted
```
gksu gparted
```

---

