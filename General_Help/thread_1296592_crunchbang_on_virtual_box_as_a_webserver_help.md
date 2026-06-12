---
title: "crunchbang on virtual box as a webserver help"
date: 2009-10-20
forum: General Help
---

### Post by holycow131415 on 2009-10-20
Hey guys,

I installed xampp, and localhost works. The host system is windows vista, and the guest system is crunchbang. Im trying to access the webserver from vista with the ip adress behind our router (192.168.1.102), which is my vista ip address. the ip adress that crunchbang has is 10.0.2.15 . Both IPs dont work when entered in vista, and only crunchbangs IP works within itsself. i installed gufw firewall, and the firewall is off for testing reasons so that i dont have to worry about allowing port 80, so i am out of ideas on how to make the website accessible through my home network, and then in the future, accessible to the internet.

---

### Post by holycow131415 on 2009-10-21
Anyone?

After some research, I've learned that I have to port forward from virtual box's [documentation]("http://www.virtualbox.org/manual/UserManual.html#natforward"). This doesn't explain it to me too well, can someone explain the lines of code?

```
VBoxManage setextradata "Linux Guest"
      "VBoxInternal/Devices/pcnet/0/LUN#0/Config/guestssh/Protocol" TCP
VBoxManage setextradata "Linux Guest"
      "VBoxInternal/Devices/pcnet/0/LUN#0/Config/guestssh/GuestPort" 22
VBoxManage setextradata "Linux Guest"
      "VBoxInternal/Devices/pcnet/0/LUN#0/Config/guestssh/HostPort" 2222
```

In Vista i actually looked at virtualbox's directory, and saw that there is no path of folders, unless its hidden, which I didnt check at the time.

---

### Post by holycow131415 on 2009-10-22
Has anyone set up a webserver using virtualbox???

---

