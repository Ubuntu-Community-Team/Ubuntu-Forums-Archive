---
title: "Problems Installing azio awu101n drivers for Ubuntu"
date: 2010-08-15
forum: General Help
---

### Post by dirtyturky on 2010-08-15
Hi i need help installing the drivers for my wireless adapter.  An azio awu101n.  I am running ubuntu 10.04 and am fairly new to linux.  So any help would be greatly appreciated as the readme file confuses me.  I get all kinds of errors when i make the driver.

Thanks

---

### Post by Frizzy350 on 2010-08-26
I'm having the exact same problem.  The read me is incredibly confusing.  Any help would be appreciated.

---

### Post by pbrstreetgang on 2010-09-17
I'm assuming you just want to get the thing to work. In that case, you just need to add rt2870sta to /etc/modules then load that module with modprobe. You can do this with:

```
sudo bash
echo "rt2870sta" >> /etc/modules
modprobe rt2870sta
exit
```I think I had to restart as well. I got this from some guy in the newegg feedback:
[URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16833340014"]
http://www.newegg.com/Product/Product.aspx?Item=N82E16833340014[/URL]

FYI, the drivers were also not compiling for me.

---

### Post by coolcar on 2012-01-13
Thanks ! I tried this code suggested. 

The Azio AWU101N wireless adapter now is able to connect to open networks.

However does not work when I try to connect to a WPA2 network on D-Link D-601 modem with DD-WRT firmware.

---

