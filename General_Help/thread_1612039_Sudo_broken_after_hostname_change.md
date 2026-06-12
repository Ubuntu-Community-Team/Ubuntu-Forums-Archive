---
title: "Sudo broken after hostname change"
date: 2010-11-02
forum: General Help
---

### Post by Crazedpsyc on 2010-11-02
I changed my hostname by running sudo gedit /etc/hostname and changing the word there. Then I discovered that hadn't done anything so I used sudo hostname newname. My hostname was changed then but I tried to run sudo gedit /some/thing/else.txt and it said:
```
sudo: unable to resolve host newname
No protocol specified

(gedit:5512): Gtk-WARNING **: cannot open display: :0.0

```
and it says the same with sudo or gksudo for any program that has a gui including synaptic. I can run vi but I have no idea how to use it. I think the problem lies in the lines in /etc/hosts which still say 
> 
192.168.1.10    ubuntu    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    ubuntu    localhost6.localdomain6    localhost6
127.0.1.1    ubuntu.ubuntu-domain    ubuntu


with the problem being that it still says localhost and my local IP address are ubuntu instead of newname. So if you could tell me how to edit that with vi or some other command line program I hope that will fix it.
Thanks in advance!

---

### Post by Crazedpsyc on 2010-11-02
I fixed the hostname issue but I still get > No protocol specified
(gedit:6173): Gtk-WARNING **: cannot open display: :0.0
 when running sudo or gksudo gedit (or any other program)

---

### Post by Crazedpsyc on 2010-11-03
after rebooting it was fixed

---

