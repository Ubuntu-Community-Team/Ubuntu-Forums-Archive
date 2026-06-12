---
title: "wireless driver won't activate"
date: 2010-01-25
forum: General Help
---

### Post by malacoda77 on 2010-01-25
I just installed ubuntu netbook remix onto a hp mini 1116 nr.  i can get the broadcom sta driver to activate and run when boot from the usb, but not from install on the harddrive.  any ideas on how i can get this to work from the install on the harddrive?:confused:

---

### Post by c0mput3r_n3rD on 2010-01-25
Are you hard-wired to the network? and going the administrative tasks to hardware drivers?

---

### Post by malacoda77 on 2010-01-25
unfortunatley no.  i'm using an xp machine to download and run everything using a usb dongle.  i also have an ubuntu laptop at my disposal, however no hardwired network connection.:confused:

---

### Post by malacoda77 on 2010-01-25
i'm currently muching wireless:)

---

### Post by MaindotC on 2010-01-25
Your usb is probably loading the proper module and for some reason it was omitted or blacklisted when you did a full install.  I've had this happen before.  Follow the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  I'm guessing what you should do is see which module is being used on the usb installation (with the lsmod command) and then make sure that module is activated on the hard drive installation (using the modprobe command).

---

