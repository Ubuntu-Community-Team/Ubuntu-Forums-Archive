---
title: "my problem with USB E1550"
date: 2010-07-19
forum: General Help
---

### Post by ash210 on 2010-07-19
[SIZE=4][COLOR=Blue]hi to every one 

i have  USB modem huawei1550 and it work nice but i have one problem that i cant send or Receive messages  because my pc dont recognize  my usb as usb modem
so 
if any one have any idea about any prog to send and receive messages work with E1550
or any solution to my problem because i don't have any experience  in Linux:(
[/COLOR][/SIZE]

---

### Post by cym104 on 2010-07-19
**[COLOR=#8b0000]From the stick post:[/COLOR]**
**[COLOR=#8b0000][/COLOR]** 
[B][COLOR=#8b0000]Problem with Huawei and possibly other usb mobile broadband dongles.[/COLOR] 
[/B]Please see this bug report and click the affects me button if you have this bug. 
Try this first

Code:
sudo apt-get install usb-modeswitch
A fix is committed. [[COLOR=#444444]https://bugs.launchpad.net/ubuntu/+s...ux/+bug/446146[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146").
Also fix/workaround here. [[COLOR=#444444]https://bugs.launchpad.net/ubuntu/+s...ux/+bug/509547[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/509547") See post #32

---

### Post by ash210 on 2010-07-21
[COLOR=Blue]thank you
my usb is work fine but i want to send messages and receive  messages (i want it work like it work in windows ) [/COLOR]

---

