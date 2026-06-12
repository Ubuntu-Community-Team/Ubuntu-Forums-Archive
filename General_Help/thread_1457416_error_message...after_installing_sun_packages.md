---
title: "error message...after installing sun packages"
date: 2010-04-18
forum: General Help
---

### Post by travm0870 on 2010-04-18
I was trying to install a couple of the sun packages (I didn't write down the package names) and after the install I get the follow error...
 
Xsession: unable to start X session--- no "/home/username/.xsession" file, no "/home/username/.xsession" file, no session managers, no window managers, and no terminal emulators found; aborting.
 
I've done some searches on the web for other related issuses and found one that suggested....installing X... using the following code...
sudo apt-get install xserver-xorg....when I tried that from a terminal...I got this...
dpkg was interrupted, you must manually run dpkg -- configure -a' to correct the problem...any thoughts?
 
I'm running the latest version of ubuntu....just installed last weekend. 
 
 
Thanks, 
Travis

---

### Post by Bungler on 2010-04-19
Would be weird if the you do no have xorg anymore. Perhaps you can just reconfigure it?

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by oldos2er on 2010-04-19
> **travm0870 said:**
> I was trying to install a couple of the sun packages (I didn't write down the package names)

Which version of Ubuntu are you using? 

Edit: Never mind. Should've read more carefully.

Exactly how were you trying to install these packages? If you were using terminal commands, could you please post them here (use up arrow in terminal to review commands)?

---

