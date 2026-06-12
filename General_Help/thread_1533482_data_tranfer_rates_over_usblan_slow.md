---
title: "data tranfer rates over usb/lan slow"
date: 2010-07-18
forum: General Help
---

### Post by BULLIT22 on 2010-07-18
Hello folks,

I am running ubuntu 10.4 lts desktop and ubuntu 9.10 server with the gui active. On both of these machines the data transfer rates over usb and lan have slowed down quite considerably. Also over multiple devices, not the same hardware everytime I try to transfer something. Anybody have any ideas? Let me know if you would need some other info. Thanks.

---

### Post by TechBeastie on 2010-07-18
The first thing I'd suggest is that you check your system logs for any and all messages related to USB and/or LAN traffic.  You can pipe the dmesg command through grep, like so ```
 dmesg | grep [word you're looking for] 
``` to help you with this process.  (dmesg displays the contents of the rotating kernel log; grep just searches for a specified word or phrase).  
Of course, you can also just run dmesg by itself, but that will produce a LOT of output.

---

### Post by BULLIT22 on 2010-07-20
Thanks for the reply. Although I am fairly new to linux, I have no idea what it is you are talking about, sad to say. Is there any way you could guide me along? Sorry. Also seems to be slow via streaming to my xbmc live pc. Thanks for the help by the way...

---

