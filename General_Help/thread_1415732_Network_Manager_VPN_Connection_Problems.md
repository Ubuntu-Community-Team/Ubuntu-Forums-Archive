---
title: "Network Manager VPN Connection Problems"
date: 2010-02-25
forum: General Help
---

### Post by Coding Monkey on 2010-02-25
Hi Everybody

I've set up a pptp VPN connection using the Network Connections GUI in Intrepid.  I can see the VPN under "VPN Connections" if I click on the Network icon on my task bar, with a little white circle next to it.  However, if I click on the VPN, absolutely nothing happens.  Could someone please tell me what's going on?  I'd really appreciate some help in connecting to the VPN.  Thanks a lot guys!

---

### Post by lotharmat on 2010-02-25
What kind of VPN is it?

to use the CISCO one you need to install VPNC

```
sudo apt-get install vpnc
```

I think the other is Open VPN

---

### Post by Coding Monkey on 2010-02-25
Hi lotharmat

Thanks for your reply.  It's a PPTP connection.

---

### Post by prostar on 2010-02-25
I just had this problem. I did a "complete removal" of the cisco components (vpnc, network-managaer-vpnc) and it went further.

Check [this thread]("http://ubuntuforums.org/showthread.php?t=1348974") for further problems (solution near the end?)

---

