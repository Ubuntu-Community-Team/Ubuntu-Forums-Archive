---
title: "need help with startup script"
date: 2011-05-12
forum: General Help
---

### Post by zogthegreat on 2011-05-12
Hi everyone,

I need some help with startup script. I have a problem with an error on system boot:

hub 2-0:1.0:unable to enumerate usb device on port 5

This error is continuous, filling up my system logs. It is also a known kernel bug. I found a solution here:

[http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/](http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/)

but it is only good after I boot. I have tried to make a startup script in /etc/init.d  in the following manner.

sudo mkdir /opt/usb/ 
sudo gedit /opt/usb/usbproblem.sh 
 
#!/bin/bash 
# chkconfig: 345 91 19 
# description: stop usb problem on startup 
 
case $1 in 
*) 
 
    echo "fixing usb problem"  
cd /sys/bus/pci/drivers/ehci_hcd 
sh -c 'find ./ -name "2-0:1.0" -print| sed "s/\.\///">unbind' 
cd ~ 
 
esac 
exit 0 
#End of boot script 
## 
 
sudo cp /opt/usb/usbproblem.sh /etc/init.d 
cd /etc/init.d 
sudo chmod +x usbproblem.sh 
sudo update-rc.d usbproblem.sh defaults  92 20 

but it does not work. 

Does anyone know where I am messing up?

BTW, running Ubuntu 11.04

zog@phoenix:~$ uname -a
Linux phoenix 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Thanks

zog

---

