---
title: "Highly weird wireless problem"
date: 2011-01-02
forum: General Help
---

### Post by sr.philosophy on 2011-01-02
I have an Ubuntu 10.04. It connects perfectly with a Netgear wireless to the internet at my work place. But i cant connect it to my home Netgear network. It connects to the router. Receives IP address. But no internet. But I'm able to connect to internet using ethernet. I'm also able to connect to internet wireless in my Windows.

---

### Post by Pithikos on 2011-01-02
What's your wifi card model? Maybe you should try the proprietary drivers for linux. Had the same problems and that worked for me.

---

### Post by sr.philosophy on 2011-01-02
But the same works on another network at my workplace.

---

### Post by Gunman1982 on 2011-01-02
Are you using a router at home which uses the n-type network? Some cards/drivers still have problems with that under linux.

The output of the command 'lspci' (execute in a console) would give us some more information to help you. Especially the line with your wireless card.
i.e.: 03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

---

### Post by WlaadDyaab on 2011-01-02
Hi

I've had the same problem when I used to use Windows XP as my main operating system

The problem for some reason was that the security level of my Netgear router was too high

I went back to the main computer that could edit my router settings; entered my username and password, and found out that I had ticked the "WPA-PSK [TKIP] + WPA2-PSK [AES]" (which is the highest security level and has really long password)

So I changed it and ticked either "WPA2-PSK [AES]" or "WPA-PSK [TKIP]"

The Internet's fine now. My Netgear router is now giving Internet access to 2 Laptops and and 2 PCs

I hope that helped :)

---

### Post by melander on 2011-01-02
> **sr.philosophy said:**
> It connects to the router. Receives IP address. But no internet. But I'm able to connect to internet using ethernet. 

Could it be a problem with name resolution?

Can you ping your router (assuming the default Netgear IP of 192.168.0.1)?

```
ping 192.168.0.1
```

Can you ping an external IP address?

```
ping 8.8.8.8
```

Can you ping Google?

```
ping google.com
```

What's in your resolv.conf?

```
cat /etc/resolv.conf
```

For some reason, Meerkat blanked my resolv.conf when it installed over Lynx and I just edited the file manually to add a couple nameservers.

Regards,

---

