---
title: "repair ubuntu os 9.1"
date: 2010-04-01
forum: General Help
---

### Post by farchumbre on 2010-04-01
hi
i uninstall compiz and meta city.
i can only run the terminal now.
how can i get internet connection thru the terminal so i will be able to re install them?
or how can i use ubuntu cd to repair the damage?
thanks

---

### Post by kokkus on 2010-04-01
Just because you removed the metacity and compiz packages doesn't mean your internet connection is gone. Or didn't you have the internet connection in the first place? If you have internet connection you can simply install compiz and metacity from the terminal by using apt-get.
Or you can press ALT+F2 and type in synaptic.
When you are in synaptic you can install the packages again.
If you for some reason do not have internet connection, reboot and open up recovery mode to install the packages again.

---

### Post by nothingspecial on 2010-04-01
For wired connection
```

sudo ifconfig eth0 up
sudo dhclient
```

---

