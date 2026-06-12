---
title: "Static IP Address Question:"
date: 2009-09-18
forum: General Help
---

### Post by wbee on 2009-09-18
Hello,

((JJ,32,up to date))

Using the monitors applet in the upper right hand corner,I went,icon>wired>add>IPv4 settings>manual> and added an address,net mask,and gateway.

Following the lead of how I had set up a static address in Windows XPmedia edition for the ip address,I added a number suffix to the ip address. Then,adding the net mask and the gateway,I was one digit short of room,and the "apply" button would not engage.

So,I tried again,this time adding the true number for the ip address,the net mask and the gateway.

It accepted it and labeled it as "Wired Connection 1.

I rebooted and everything is fine.

So,when I go into my router to let through a port,should I enter the ip number or the "broadcast" number as the "static" address?

((Yes,I know the automatic function is probably easier,but I'm curious about this.))

------------

Thank you.

---

### Post by Shujah on 2009-09-18
The address as in address you gave in manual setting.

---

### Post by Dantheman53 on 2009-09-18
The ip address

if you're not sure what it was, type in terminal

> ifconfig

Under eth0 you should see a line that say something like this


inet addr:192.168.0.10

---

### Post by wbee on 2009-09-18
Thank you both.

---

