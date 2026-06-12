---
title: "installation 12.04"
date: 2012-05-08
forum: General Help
---

### Post by CoyoteUK5 on 2012-05-08
Helllo

I have had linux mint 10 on my machine although it works well I thought I would try ubuntu 12.04.
When I was experimenting with it ( pre install ) everything was fine, so I installed it side by side with mint.
Then after rebooting and entering 12.04 it now seems I have no internet in ubuntu but in going to mint everything works fine.
Anyone got any ideas or suggestions what I should do.

Regards

Coyote

---

### Post by dino99 on 2012-05-08
which resolvconf package is installed ?

The latest 1.63ubuntu13 from precise-proposed breaks my network too, but ubuntu12 works fine.


sudo dpkg -i /var/cache/apt/archives/resolvconf_1.63ubuntu12_all.deb (or ubuntu11, depending of which one you have)
(if you have it already there)

or pick it from Mint

note: you should deactivate precise-proposed into synaptic, then update again (sudo apt-get install synaptic)

---

### Post by smurphy on 2012-05-08
Another possibility is to configure the network statically.
Works here without workaround...
IMHO the dhcp bit or network manager automation (under KUbuntu) is broken.

---

### Post by hyperreal on 2012-05-08
> **CoyoteUK5 said:**
> Helllo

I have had linux mint 10 on my machine although it works well I thought I would try ubuntu 12.04.
When I was experimenting with it ( pre install ) everything was fine, so I installed it side by side with mint.
Then after rebooting and entering 12.04 it now seems I have no internet in ubuntu but in going to mint everything works fine.
Anyone got any ideas or suggestions what I should do.

Regards

Coyote

First kill the network-manager applet.
```

$  sudo killall nm-applet

```

Now make sure your network-manager service is running.
```

$  sudo /etc/init.d/network-manager start
or
$  sudo service network-manager start

```

Now start nm-applet again:  press ALT-F2 and enter this command:
```

sudo nm-applet

```

If you network ESSID isn't showing, then you may have a driver issue.  In this case, type
```

$  lscpi

```
into the terminal.  Copy and paste all the output into a new reply in this thread, and I'll see what I can do from there.

---

