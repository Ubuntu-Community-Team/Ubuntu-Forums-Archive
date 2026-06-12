---
title: "Hybrid Graphics"
date: 2011-07-30
forum: General Help
---

### Post by Elitenoname on 2011-07-30
Ok so I have found the help doc in the ubuntu  community spot and it says to run the following command,

```
grep -i switcheroo /boot/config-2.6.*
```

And I do that and nothing happend, so i though ok maybe i missed something and moved to the next step to see if the switch file is there and I do,

```
ls -l /sys/kernel/debug/vgaswitcheroo/switch
```

Says the file can not be found, and according to the post on the community help spot VGA_Swicheroo is not enabled, well my problem is how do i enable it and use it?

---

### Post by Z06Gal on 2011-07-30
Do you have Nvidia Optimus?  I use my Intel integrated and enable my optimus for graphics with bumblebee.  It works quite well actually but it is only for laptops with optimus as far as I know.  ;)



Robin

Edit:  This may help you out - [http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)

---

### Post by Elitenoname on 2011-07-31
yea it says it does but the card is a ion next gen graphics card by nvidia

---

