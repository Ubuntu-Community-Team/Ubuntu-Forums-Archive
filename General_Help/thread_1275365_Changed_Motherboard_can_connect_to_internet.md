---
title: "Changed Motherboard can connect to internet"
date: 2009-09-25
forum: General Help
---

### Post by roundhay on 2009-09-25
I had to change the MB and CPU in my server after the original MB broke.

I have connected the old HDD containing Ubuntu Server 8.10 and can boot but I can't connect to the internet, host google.com time's out and does not find hosts.

(I have booted the system using a copy of the desktop edition on a USB stick and can use the internet and all other parts of the system seem to be OK.)

When I run ifconfig I don't see eth0 only vnet0 and lo

I don't know what vnet0 is? I don't have vmware installed (this has been mentioned in other posts)

I'm not sure what I have should do next? Do I need to recompile the kernel? I have looked at this and most of the how-to's assume you have an internet connect which is a problem for me.

Could I reintall the kernel from the original install CD?

---

### Post by VipX1 on 2009-09-25
Did you install a replacement motherboard of the same make and model as the faulty one??
An operating system is set up during installation to run with a particular motherboard, drivers etc. So, is it new motherboard the same model as the old, broken motherboard?

---

### Post by roundhay on 2009-09-25
I had an old Asus duel CPU board and I have changed to a new Gigabite G31 board. I know this will be the problem but I want to know if there is a way of updating / recompiling the current system or will I have to do a fresh install?

---

### Post by linux_tech on 2009-09-25
What network adapter is it?

---

### Post by roundhay on 2009-09-25
Here is a link to the board [http://www.gigabyte.com.tw/Support/Motherboard/CPUSupport_Model.aspx?ProductID=3134]("http://www.gigabyte.com.tw/Support/Motherboard/CPUSupport_Model.aspx?ProductID=3134")

---

### Post by zipperback on 2009-09-25
> **roundhay said:**
> 
When I run ifconfig I don't see eth0 only vnet0 and lo



Please provide the output of the following:
```

lsusb
lspci
ifconfig
iwconfig

```

What kind of network card did you install in the computer?
Are you sure the network card in question is correctly working hardware and that it is fully supported under Linux?

- zipperback
:popcorn:

---

### Post by dcstar on 2009-09-26
> **roundhay said:**
> I had to change the MB and CPU in my server after the original MB broke.
........
When I run ifconfig I don't see eth0 only vnet0 and lo
........

Changing hardware can create a new designation - like eth1 - that needs configuration.

Go into System-Administration-Network and see if you can create a new connection.

---

### Post by roundhay on 2009-09-26
I have managed to get the box onto the net by upgrading to 9.04 and then using the recovery option at login to fix all of the broken packages

Not exactly what i wanted to do but I can now use the system again and can transfer the files I want from the server if i decide to upgrade.

---

### Post by dcstar on 2009-09-26
> **roundhay said:**
> I have managed to get the box onto the net by upgrading to 9.04 and then using the recovery option at login to fix all of the broken packages
.......

All that did was auto-detect the LAN settings on the Live CD and then run through the same hardware auto-detect procedures in the new version upgrade - thus overwriting the old settings for the previous motherboard.

A very time-consuming procedure to fix a simple problem.

---

