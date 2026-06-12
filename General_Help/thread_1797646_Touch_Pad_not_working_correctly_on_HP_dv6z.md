---
title: "Touch Pad not working correctly on HP dv6z"
date: 2011-07-05
forum: General Help
---

### Post by blue677 on 2011-07-05
I have an Hp Pavilion dv6z laptop and I am having some trouble getting the touch pad to function correctly.   The right click function on the touch pad does not work and the touch pad will not highlight things.  I have tried using this:

```
sudo su
```
```
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe

```
```
reboot
```

 without any luck.

Any help would be appreciated.

---

