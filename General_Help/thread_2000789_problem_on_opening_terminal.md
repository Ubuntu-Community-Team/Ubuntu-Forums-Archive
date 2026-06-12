---
title: "problem on opening terminal"
date: 2012-06-10
forum: General Help
---

### Post by samaresh on 2012-06-10
Computer partially hang up when I open **terminal** .This problem temporarily gone if I delete all **bash history** . 
    Partially hang up means unity launcher , window maximize , minimize ,close button ,  mouse scroll , mouse left click on folder works fine but unity dash, keyboard , mouse right click , mouse click on menu not working.
  I am using **Ubuntu 12.04 64 bit**
  Please help.

---

### Post by papibe on 2012-06-10
Hi samaresh.

It could be either a gnome-terminal problem, or a bash problem. One way to find out would be to load another terminal, for example xterm.

If that also freeze for a while, then I would turn into bash itself.

Open a either terminal, and once it's unfrozen run this:
```
bash
```
If you experience the problem again, it means some of the bash configuration files is running something on its initialization. 

If you confirm that, the first thing I would do is to reset your ~/.bashrc

To do that run this:
```
cp  ~/.bashrc  ~/.bashrc.old

mv /etc/skel/.bashrc ~/.bashrc
```
I hope it helps, and tell us how it goes.
Regards.

---

### Post by samaresh on 2012-06-11
Thanks for reply.
I have also used **xterm** . But the problem remain same.
Fortunately, this problem gone automatically for unknown reason.

---

