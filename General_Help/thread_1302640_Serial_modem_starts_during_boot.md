---
title: "Serial modem starts during boot"
date: 2009-10-27
forum: General Help
---

### Post by AlP36 on 2009-10-27
I just installed Hardy (second try) and everything is working like it should, except the modem. It starts dialing before the username screen comes up. That leads me to think it is in the Grub somehow.
I have Ubuntu 6.06 still on one disk and XP on another with Hardy on the second disk. Since I did this install the modem starts in both Ubuntu versions during the boot process. Also, the Modem Monitor does not work in Hardy and it is reversed in 6.06 (that is- when the system finally boots I  have to enter a password to disconnect;)).
I have setup the connection in Network and as you can see I connect to the right place. In Hardy the only way to disconnect is to turn off the modem. 
Any ideas for me?

---

### Post by dcstar on 2009-10-27
> **AlP36 said:**
> I just installed Hardy (second try) and everything is working like it should, except the modem. It starts dialing before the username screen comes up. That leads me to think it is in the Grub somehow.
I have Ubuntu 6.06 still on one disk and XP on another with Hardy on the second disk. Since I did this install the modem starts in both Ubuntu versions during the boot process. Also, the Modem Monitor does not work in Hardy and it is reversed in 6.06 (that is- when the system finally boots I  have to enter a password to disconnect;)).
I have setup the connection in Network and as you can see I connect to the right place. In Hardy the only way to disconnect is to turn off the modem. 
Any ideas for me?

It has absolutely nothing to do with Grub, it is because of the network configuration you have in the system.

---

### Post by AlP36 on 2009-10-27
> **dcstar said:**
> It has absolutely nothing to do with Grub, it is because of the network configuration you have in the system.

Thanks David- could you give some specifics as to what may be incorrect in the Network setup? I have taken out the "Use Modem as Default Connect to  Internet" as suggested in: [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto). That killed the connection but did not stop the auto dialing. 
Also, does anybody use the "Modem Monitor" applett? I have used it for a couple of years in 6.06 with no real problems but in Hardy the activate and deactivate are greyed out so I can't use it at all.

---

