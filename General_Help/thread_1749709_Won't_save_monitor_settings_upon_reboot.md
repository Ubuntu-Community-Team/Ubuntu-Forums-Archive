---
title: "Won't save monitor settings upon reboot?"
date: 2011-05-04
forum: General Help
---

### Post by webcabbie on 2011-05-04
So I have a fresh updated install of 10.10 on dell dimension 4550

The pc connects to my monitor through a dlink KVM switch so I can switch back and forth between computers.

When I reboot my monitor settings disapear and everything is real real large. 

If i disconnect from the KVM and connect Ubuntu directly to the monitor and detect monitor it will allow me to adjust settings so everything looks normal. Until I reboot and I am back to the same huge icons again. If I try to go back and adjust monitor settings there are only 2 settings options because it does not see my monitor through the kvm switch again. 

Any help here guys?

---

### Post by webcabbie on 2011-05-04
ok I am reading a possible solution is to edit my xorg .conf file can someone help me with this? I dont wanna mess my **** up.

---

### Post by seawolf167 on 2011-05-04
Try running 

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by webcabbie on 2011-05-04
i did that and nothing happened. Was I supposed to do that in conjunction with some other thing?

---

### Post by seawolf167 on 2011-05-05
Do you have any/all necessary hardware drivers installed for your device? Check system - administration - hardware drivers and install the drivers for your device

---

