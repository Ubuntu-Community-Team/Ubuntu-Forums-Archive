---
title: "How to backup my (transfer to desktop) data on a netbook to restore the system?"
date: 2009-08-16
forum: General Help
---

### Post by Repgahroll on 2009-08-16
Hello!

I have an aspire one which seem to be broken... the wireless used to work very well but some days ago it stopped working for some boots and now it simply doesn't work anymore... i tried a lot of things, like the madwifi modules, a vanilla ubuntu jaunty, moblin (latest), the karmic alpha4, and the thing simply doesn't work... lspci shows it and if i try to connect to a hidden network the led blinks. But it doesn't find any networks at all.

So i decided to restore the default linpus system, but i have a lot of data on the 160-GB mini hd, and i can't lose that.

Also, i have a desktop pc running Ubuntu 9.04 64-pid and Windows XP Professional, there are plenty of blank space on HD and i could surely use it to backup the whole netbook HD, however, i don't know what's the best (easy/quick) way to do that... i have a lot of rj45 cables (i have a dsl-modem connected to a wireless router connected by wire to 2 other pcs, and i could use the cables) and i think it should be nice to use a ethernet connection to transmit the data.

Can someone help me please?

Thank you for your time.

---

### Post by Repgahroll on 2009-08-17
Please guys... i just want to know a way to transfer my files to my desktop using a rj45 cable.

Thanks.

---

### Post by nikhilk on 2009-08-17
If you have a crossover RJ45 cable you can connect the two machines directly, no router required at all. This, therotically, should be the fastest way since no router delay would be involded (however small that might be). Just assign static IPs to both machines temporarily and you should be able to connect directly using the static IPs.

Otherwise you can connect them through the router which will be quite simple as well.

---

### Post by Repgahroll on 2009-08-17
Thank you very much!

However, isn't necessary to setup some kind of "server" on the machine that will upload the files?

Is it easier to use the Windows XP or Ubuntu installation on desktop?

---

### Post by nikhilk on 2009-08-17
> **Repgahroll said:**
> However, isn't necessary to setup some kind of "server" on the machine that will upload the files?

Is it easier to use the Windows XP or Ubuntu installation on desktop?

You can run a NFS server on your netbook and download the files to your desktop. [Here]("http://ubuntuforums.org/showthread.php?t=249889") is a good NFS setup thread by malco2001.

---

### Post by Repgahroll on 2009-08-17
Ah, OK man! Thank you very much for your help, and i'm marking this topic as solved! :D

---

### Post by nikhilk on 2009-08-17
> **Repgahroll said:**
> Ah, OK man! Thank you very much for your help, and i'm marking this topic as solved! :D

You are welcome!

Just forgot to answer your earlier question, use Ubuntu on your desktop, hey these are the Ubuntu forums :)
Actually with NFS both machines should be running Linux.

---

