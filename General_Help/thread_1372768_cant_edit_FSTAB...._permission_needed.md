---
title: "cant edit FSTAB.... permission needed???"
date: 2010-01-04
forum: General Help
---

### Post by mvalenti on 2010-01-04
I am trying to do get my iPhone working and have hit a roadblock....


Trying to do this:
((The output should be a number. Now edit /etc/fstab and add the following line, but make sure you set the devgid= number to the output of the previous command.))


Adding this line to fstab...
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0 

cant save the file after editing with gedit...

am I missing something simple?

---

### Post by mechro on 2010-01-04
... requires root permissions.

In a Terminal do...

**gksudo gedit /etc/fstab**

PS. back-up/copy your fstab first.

---

### Post by WorldTripping on 2010-01-04
You need to be sudo.

So I use 'sudo nano /etc/fstab'

hth

WorldTripping

---

### Post by WorldTripping on 2010-01-04
ninja'd

---

### Post by mvalenti on 2010-01-04
> **mechro said:**
> ... requires root permissions.

In a Terminal do...

**gksudo gedit /etc/fstab**

PS. back-up/copy your fstab first.

Much appreciated! I was trying sudu gedit....

What does the gk prefix do? I couldnt find it in my Ubuntu toolbox book...

---

### Post by mechro on 2010-01-04
Use gksudo if it's to open a graphical/gui application like nautilus or gedit and so on.

---

### Post by mvalenti on 2010-01-05
thanks for the help! all is working!

---

