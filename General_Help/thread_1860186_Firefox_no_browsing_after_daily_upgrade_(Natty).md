---
title: "Firefox: no browsing after daily upgrade (Natty)"
date: 2011-10-14
forum: General Help
---

### Post by pa3fat on 2011-10-14
Just upgraded with the available updates. Decided to skip upgrading to Oneric.

After this rebooted the system.

Tried to use firefox but keep getting can't find server. No webpage shown.

The wireless connected laptop (using it now) is still working so doesn't look like general DNS issue.
Also Transmission is running and down/uploading. Not a general connectivity issue.

Any tips to restore browsing with Firefox on Ubuntu (Natty)?

Thanks in advance for you help.

Ron

---

### Post by pa3fat on 2011-10-14
Rebooted and checked connectivity.
Still no improvement.

Also disabled IP6 on the Eth0 adapter. No improvements.

Reinstalled Firefox and rebooted. No improvements.

Any options to check DNS resolving in Ubuntu? E.g. what is the command.
Same as on Win? Tracert?

---

### Post by pa3fat on 2011-10-14
Tried ping to a known working url e.g. [www.nu.nl]("http://www.nu.nl")

No DNS resolve is taking place.

What is the cause of this?
Checked connection details and the gateway is 192.168.1.1


It is still working on my W7 laptop.....

What is causing DNS not to work???

And how to resolve this sudden situation???

---

### Post by effenberg0x0 on 2011-10-14
What do you have on /etc/resolv.conf?

As a test, add there:
```
nameserver 8.8.8.8
nameserver 4.4.4.4
```

Save the file, try to ping and dig domains.
This google nameservers will be removed from there by NetworkManager the next time you boot. You should receive proper DNSs from your DHCP server. NetworkManagers gets the DNSs information when it connects to a network via DHCP and put them inside /etc/resolv.con until you connect to another network (new dhcp, new dns, etc).

Regards,
Effenberg

---

### Post by pa3fat on 2011-10-14
Hi Effenberg,

Thanks for your reaction. Was upstairs working on the Ubuntu machine.

And actually found the cause (even this noob could)

The resolv.conf was totally empty.

Edited (googled around first with the laptop) and added the nameserver info 192.168.1.1.

As i had IP6 disabled i switched it on.
nameserver turned into ip6 notation, but at that point it didn't work anymore (i used to before upgrade with the updates !!)

So now manually switched back to IPV4 nameserver 192.168.1.1 and keep IP6 switched off for now.

But it is really strange that it stopped working. As only updates were pulled using update manager this evening.

That the resolv.conf was totally empty is also strange.

Gigabit network and never had any issues with it.

If you need me to check more to structurally resolve this issue. Please let me know.

And thanks a lot for responding !

---

### Post by effenberg0x0 on 2011-10-14
Check that you have network-manager, and its dependencies, properly installed. Normally, when you do, resolv.conf is managed by it. If you use nm-applet too connect to some wireless network, it will receive new DNSs via DHCP and push them to resolv.conf. As you switch to another network, same process will happen.

But if you remove network-manager and not connect to your lan/wlan using dhcp client, resolv.conf would be empty.

Regards,
Effenberg

---

### Post by pa3fat on 2011-10-14
Will reinstall networkmanager. But did nothing in this area. Only applying the pending updates via updatemanager.

After that i detected the issues.

Running ubuntu as e.g. NAS server. FTP/Transmission/Shares. So nothing else after basic install some 3-4 weeks ago.
Monitored the (pre-)release issues of Oneric and explicitly did not upgrade yet. Unfortunatly Transmissioin 2.41 is causing remote gui issues and the DNS issues we are trying to tackle currently. That IP6 also stopped working is also strange.
But that is not that important for now. 

Tnx for helping.

---

### Post by pa3fat on 2011-10-15
Reinstalled NetworkManager via Synaptic.
Rebooted.

And again resolv.conf is totally empty.

File is owned by root:root rw-r-r-r

Think something is wrong in the system. How to resolve this structurally?

Disconnecting from network and applying settings via gui also does not resolve it.

---

### Post by pa3fat on 2011-10-16
Think i found the cause.

For IP4 you have 
- Automatic DHCP
- Automatic DHCP addresses only.

Last one was the default.

I switched to Automatic DHCP. 
And now i get IP4 and IP6 nameserver data in resolv.conf

After reboot all ok now.

---

