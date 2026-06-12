---
title: "TP Link PCI Lan card installation problems"
date: 2012-06-12
forum: General Help
---

### Post by itbookham on 2012-06-12
Hello,

I am new to this Forum, and the wonderful world of Linux, and hello to everyone.

I have just installed Ubuntu Desktop on my computer. The installation went well, but the install didn't install the drivers for 2 PCI TP-Link TF-3200 Lan Cards.

A CD came with the cards which has a folder 'Linux Drivers'. But reading through the readme.txt I have to say I am completely bewildered by the complexity of installation. Please see some of the procedures below:

-----------------------------------------------------------------------------------------------------------------------

automatically load and configure at next boot time 
   ----------------------------------------------------- 
     c1. cp sundance.o /lib/modules/`uname -r`/kernel/drivers/net 
     *note: The `uname -r` is a command. Don't replace `uname -r` with 
            2.4.18, 2.4.20smp, or some others. Must type `uname -r` directly. 
 
     c2. Add the following lines at /etc/modules.conf: 
                
          alias eth0 sundance 
          options sundance <optional parameters> 
                               
     c3. Run "netconfig" or "netconf" to create configuration script  
 
              ifcfg-eth0 located at /etc/sysconfig/network-scripts or  
              create it manually. 
              [see - Configuration Script Sample] 
 
     c4. Driver will automatically load and configure at  
              next boot time. .....

-----------------------------------------------------------------------------------------------------------------------

I would be very grateful for assistance in installing the software drivers.

Many thanks,
Mark

---

### Post by Cheesehead on 2012-06-12
Please open a terminal window, type the command 'lspci -v' and post the result here.

---

