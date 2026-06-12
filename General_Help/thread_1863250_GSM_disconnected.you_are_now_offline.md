---
title: "GSM disconnected.you are now offline"
date: 2011-10-17
forum: General Help
---

### Post by nys on 2011-10-17
I have started using linux **ubuntu 10.04** two days before only.I am just a new comer.I have written the codes for my **huawei e1550** usb mobile broadband in the terminal.It was working fine at first.When i clicked on the broadband connection name on the network manger,the internet is disconnected and its not possible for me to connect again.so please help me.my laptop is vaio **vpceb24en**.
The code which help me first i am showing below.

1.First i wrote this in terminal $ sudo vi /etc/udev/rules.d/15-huawei-155x.rules
2.Then i wrote SUBSYSTEM=="usb",
ATTRS{idProduct}=="1446",
ATTRS{idVendor}=="12d1",
RUN+="/lib/udev/modem-modeswitch --vendor 0x$attr{idVendor} --product 0x$attr{idProduct} --type option-zerocd"

then saved and quit.after that i surfed the internet for sometime.then i disconnected.so please help me to connecct it again.
and one more thing..i have written something something manything in the terminal whatever i saw in forum for solving the problem..

---

### Post by alexfish on 2011-10-18
hi and welcome to the forum

can have a look through this thread 

[How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

read through post :#1 carefully ,then have a look through rest of thread

any problems can post back here 

regards

alexfish

---

### Post by Larkspur on 2011-10-18
If you are able to connect by another means, you should download usb-modeswitch from the repositories.  10.04 was the last version that didn't have it by default.  Once installed, it allows your dongle to connect without any further input from you.

---

### Post by nys on 2011-12-22
thnx for ur reply...
but i didnt try it bcoz nw i have installed ubntu 11.10..nw i am not facing that problem...anyhow thnx for ur reply

---

