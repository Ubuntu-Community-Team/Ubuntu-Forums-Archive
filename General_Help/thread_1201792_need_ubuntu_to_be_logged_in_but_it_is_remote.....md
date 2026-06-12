---
title: "need ubuntu to be logged in but it is remote...."
date: 2009-07-01
forum: General Help
---

### Post by tatt on 2009-07-01
I have an ubuntu hardy machine setup which is locked away and without a screen. Also it is remote and I am unable to access it physically.

I have a working vpn as pptp to this machine and can connect and use its fileserving capabilities.

Whilst connected to its vpn I carried out a port scan and found the following ports open.....

21,53,139,445 and 1723.

Now, I had a remote desktop connection to this machine via the vnc method working, but I neglected to set the login manager to automatically login. I carried out some remote maintenance which required a reboot. The machine has now rebooted but is obviously sat at its login screen and I have now discovered that vnc will not connect until the machine is logged in. I have access to all of its samba shares but this does not include any writeable root permissions, Also i can connect to its ftp server on port 21 and can see the entire filesystem including root, I just have no write permission as root account is disabled on ubuntu.

How can I get this box logged in?????

Chris

---

### Post by t4thfavor on 2009-07-01
Have somebody on site plug a usb keyboard in it, and really carefully log it in without a monitor.

Aside from that, you have no remote management ports open, so unless your really good at finding remote root exploits you sunk.
EDIT:
Never deploy a headless machine without openssh.

If openssh is installed, you may be able to modify configs using FTP if you have it set up that way.

---

### Post by wojox on 2009-07-01
try you web browser

[http://server : port](http://server : port)

---

### Post by t4thfavor on 2009-07-01
Doesn't appear to be any web browserable services running, Looks like avahi, samba, pptp, and FTP.

I still say sunk.

---

