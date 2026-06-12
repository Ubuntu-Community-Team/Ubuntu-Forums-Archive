---
title: "Firefox extremely slow to find web pages"
date: 2009-11-19
forum: General Help
---

### Post by beckfield on 2009-11-19
I've searched a bit, but haven't found anything quite like this.

I recently upgraded to Ubuntu 9.10, and installed Firefox 3.5.5 from Synaptic.  Ever since then, Firefox has been extremely slow to find any website.  It is always "looking up www.xxx..."  It may eventually find it, and it may not.

At first I was blaming my cable internet provider, but I have a Windows Vista system sharing the connection via a router, and Firefox 3.5.5 on Windows is as fast as ever.  Also, Thunderbird has no difficulties on the Ubuntu system, and I haven't found anything else that has trouble connecting to the web.

I have completely removed Firefox and all its plugins and reinstalled, but no change.  I really don't know what else to try.

Any advice would be appreciated.

---

### Post by dmglouis on 2009-11-19
It might have something to do with how your router relays the DNS servers to your computer. I recommend you go to your router's page, see the DNS servers it uses from your ISP, and then manually add them to Network Connections like so:

Right click on Network Connections, then click Edit Connections. Then select the the connection you are currently using and press edit. Under the IPv4 tab, select Automatic DHCP (addresses only), and put in the two DNS entries from your router page.

This is only a stopgap measure. When this problem happened to me, the real problem was that my wireless card drivers were buggy with WPA2 Personal Networks. I recommend you search around for connectivity issues with the particular wired/wireless card you have.

To check the card, you can use the following:
```
sudo lshw -short | grep network
```
(Note: The above method to check my card works for me, but if someone can post a more common method, that would be nice, because I only saw this while searching for such a command a few minutes ago)

---

### Post by lovinglinux on 2009-11-19
See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

---

### Post by dcstar on 2009-11-19
> **lovinglinux said:**
> See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

Or disable IPv6 in the underlying Ubuntu system.

---

### Post by beckfield on 2009-11-19
Thanks everyone.  I'll try these this evening.

---

### Post by stroyeror on 2011-01-29
I am having the same issue,  I have tried the above and im still haveing the the issue any ideas?

---

