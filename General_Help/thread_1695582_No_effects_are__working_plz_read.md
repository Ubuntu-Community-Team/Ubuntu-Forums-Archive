---
title: "No effects are  working plz read"
date: 2011-02-26
forum: General Help
---

### Post by NoLa245 on 2011-02-26
Ok i downloaded compiz enable the effects and non of them  r working plz help.

---

### Post by sikander3786 on 2011-02-26
Welcome to the forums :-)

Did you install the graphics drivers for your card under System > Administration > Hardware/Additional Drivers?

To enable compiz, all you need to do is to Right Click your Desktop > Visual Effects Tab > Extra.

Then you can install ccsm for managing compiz effects.

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by NoLa245 on 2011-02-26
i cant find that effects tab

---

### Post by sikander3786 on 2011-02-26
> **NoLa245 said:**
> i cant find that effects tab
Apologies, my mistake. Right click the desktop > Change Desktop Background > Visual Effects Tab.

---

### Post by NoLa245 on 2011-02-26
i did all of that does not work i got to the tab choose what i want and hit keep and idk if this is the resone but i go back and it is back on nuttin

---

### Post by sikander3786 on 2011-02-26
Which version of Ubuntu is this? Also post the output of these commands from Applications > Accessories > Terminal:

```
lspci | grep VGA
glxinfo | grep vendor
```

---

### Post by NoLa245 on 2011-02-26
it is 10.10

---

### Post by sikander3786 on 2011-02-26
> **NoLa245 said:**
> it is 10.10
Please post the output of above mentioned commands to let us dig deep into your problem.

Thanks.

---

