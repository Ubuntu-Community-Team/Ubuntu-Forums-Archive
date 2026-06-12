---
title: "Connecting To Ubuntu From Windows: Remote Screen Not Refreshing"
date: 2009-11-05
forum: General Help
---

### Post by Jonah11 on 2009-11-05
I am using the latest version of Ubuntu, and the default remote desktop does not work correctly when I connect to it from my windows machine.  It connects ok, and it even registers my mouse events ok (which I can see when I have both computers in front of me), but the screen never changes on the windows machine.  This is a known problem with Ubuntu:

[http://ubuntuforums.org/showthread.php?t=470306](http://ubuntuforums.org/showthread.php?t=470306)

I tried to follow the instructions in the 2nd post of that thread, but it didn't work.  In step 3, when I issue this command:

sudo gedit /etc/X11/gdm/gdm.conf

I get blank file.  It turns out the there is no gdm directory under X11, even tho the previous steps installed correctly.  Can anyone help?  My only goal is to connect remotely, I don't care how I do it.

Thanks,
Jonah

---

### Post by Giblet5 on 2009-11-05
```
sudo gedit /etc/init/gdm.conf
```

I use Cygwin under windows (comprehensive linux tools, running native). I install the Xorg server and run an xdmcp session against remote systems.

I haven't seen a HOWTO on this... Maybe I'll write one.

It isn't difficult and it's a perfect remote desktop, just like doing it from the kdm login screen, or the Jaunty's gdm login screen.

---

### Post by Excedio on 2009-11-16
Were you finally able to get this work? I would love it if this was a success story. Then I could use it for myself.

---

### Post by 300Z on 2009-11-16
> **Excedio said:**
> Were you finally able to get this work? I would love it if this was a success story. Then I could use it for myself.

x2

---

