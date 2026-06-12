---
title: "Adding Network Manager to Menu"
date: 2011-10-13
forum: General Help
---

### Post by Theo1006 on 2011-10-13
I am using Ubuntu 10.04 LTS.
I have the Network Manager installed (as reported in the Synaptic Package Manager), but for some reason the NM does not appear in the Menu or on the top panel.
So I want to add the item to the Menu and the panel.  I am requested to browse for the command, but am at a loss what the correct command is and where to find it.
Can anyone tell me?
Thanks

---

### Post by Frogs Hair on 2011-10-13
Try the command below to restore the panel applets to default and see if the icon appears on the top panel .```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by Theo1006 on 2011-10-14
Thanks Frogs Hair!

Unfortunately this command gives the following response:
gnome-panel (1428 ): Operation not permitted
On two more attempts same response with different number: (1462), (1189)


I should explain that I am talking of my wife's laptop, of which I am admin.
When I log in as admin, I have the Network Manager icon on the top panel. But when I log in as my wife the icon is not there, even when I change her status to admin too.

How to achieve that my wife as Desktop User has the Network Manager icon also available?

Theo

---

### Post by crdlb on 2011-10-14
That is a problem in old versions of NetworkManager. Only NM 0.9 in Oneiric supports simultaneous per-user instances of nm-applet. If she logs in first, her account should have the icon.

---

### Post by Theo1006 on 2011-10-14
> **crdlb said:**
> That is a problem in old versions of NetworkManager. Only NM 0.9 in Oneiric supports simultaneous per-user instances of nm-applet. If she logs in first, her account should have the icon.

True, we are using NM 0.8.
But my wife never has the icon, she usually logs in without me logging in first.

---

### Post by crdlb on 2011-10-14
> **Theo1006 said:**
> True, we are using NM 0.8.
But my wife never has the icon, she usually logs in without me logging in first.

What happens if she runs```
nm-applet
``` in a terminal?

---

### Post by Theo1006 on 2011-10-15
@Frogs Hair:
It seems your advice worked after all, only needed a reboot.
@crdlb:
Now only the user to log in first has the NM icon, as you said. That is a minor nuisance.

Thanks all.:)

---

