---
title: "how to add module to kernel"
date: 2011-08-13
forum: General Help
---

### Post by then_dude on 2011-08-13
hello everybody,

i want to make my dvb-t usb dongle to work on ubuntu 10.04;
but i'm running kernel 2.6.38.10-general-pae. 
(this is because i'm on a sandybridge machine, and yes it is very stable and fast)

i have this dvb-t usb dongle. 
an ec168 dutv009; mxl5003 

i have found that since the 2.6.33 kernel it can be loaded as a module in the kernel. 

i have looked at my kernel config file /boot/config-(uname -r)

and found the found the entry : 
# CONFIG_DVB_USB_EC168  is not set

i changed to 
CONFIG_DVB_USB_EC168=y

so here are my questions
1)i can recompile the kernel, but that is not necessairy, since it is a module. ? true or not ?
2)if i recompile do i need to download the module first ? and if so where do you have to save it ?

3)for the moment i would like to keep the kernel "as is" and add the module. But where do i have to safe the module ? 
4)what is the extension of a module ? how do i recognize it 
5)do i have to do something with this module ?

i have found the module, or at least something which has something to do with it here :

[http://cateee.net/lkddb/web-lkddb/DVB_USB_EC168.html](http://cateee.net/lkddb/web-lkddb/DVB_USB_EC168.html)

can somebody explain me a bit what this link is and what to do with it ? 

thanks so much

(yes i have googled, but i'm to newby to get out of this rabbithole)

---

