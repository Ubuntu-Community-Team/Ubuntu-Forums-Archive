---
title: "Touchpad enabling not working Once loged in"
date: 2012-07-28
forum: General Help
---

### Post by Vishnu V on 2012-07-28
Hi,
My friend got a Acer ASPIRE E1 431, we installed ubuntu 12.04 on it, everything was fine except the touchpad.Touchpad enabling is not working once logged in without enabling touchpad (This can be done from a log in screen). But once the touchpad is enabled from login screen everything is fine, even from logged in stage we can enable/disable touchpad. We googled a lot and find a fix 
```

echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe 

```
then rebooted no problem for enable/disable key, but edge scrolling is not working. now there is no option for touchpad on "Mouse and Touchpad setting".

Please help
Thanks 
Vishnu V

---

