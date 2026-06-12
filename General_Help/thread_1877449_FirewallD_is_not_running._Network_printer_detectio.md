---
title: "FirewallD is not running. Network printer detection needs services mdns, ipp, ipp-cli"
date: 2011-11-08
forum: General Help
---

### Post by baditaflorin on 2011-11-08
I don`t need the CUPS variant with localhost. More than this, i want to disable localhost to save some momory.

I wnat to install via the Printer Applet. 

FirewallD is not running. Network printer detection needs services mdns, ipp, ipp-client and samba-client enabled on firewall.

---

### Post by darthpenguin on 2011-12-08
I get the same message running Gnome 3 on Arch. I can add printers through the CUPS interface but I'd rather not. I'd like to be able to detect printers on the network and add them with Gonme. I'm only getting that message recently. Gnome use to detect multiple Lexmark E250dn printers. I only have one but I guess it found each protocol. I wish it would aggregate all instances of the same printer into one and ask which protocol to use during setup. I haven't changed anything that I know of and I'm on the same network but it won't find any printers now. The print server is running, I can find it on my Windows VM.

---

### Post by gilgongo on 2011-12-11
I've been able to set up my printer using system-config-printer (you may need to install it if it's not on your system already). The setup wizard on that works fine.

But really, WTF Ubuntu? I'm willing to accept rough edges around non-mainstream functions in the OS, but being unable to set up a printer sucks pretty badly. Oh well at least there's a workaround.

---

### Post by Morbius1 on 2011-12-11
>  FirewallD is not running. Network printer detection needs services mdns, ipp, ipp-client and samba-client enabled on firewall.FirewallD is a Fedora daemon. Try as it might it will never find the status of FirewallD on any Debian / Ubuntu machine or any of its 3000 derivatives.

This is not Ubuntu's fault. It's not Debian's fault. It's Gnome's fault. 

The only workaround that I know of is to use system-config-printer as stated by [COLOR=Blue]gilgongo[/COLOR] above.

---

### Post by cheebhodh on 2012-04-19
> **Morbius1 said:**
> FirewallD is a Fedora daemon. Try as it might it will never find the status of FirewallD on any Debian / Ubuntu machine or any of its 3000 derivatives.

This is not Ubuntu's fault. It's not Debian's fault. It's Gnome's fault. 

The only workaround that I know of is to use system-config-printer as stated by [COLOR=Blue]gilgongo[/COLOR] above.

Thank you, the problem can be solved using system-config-printer :guitar:

---

### Post by HiImTye on 2012-04-19
if you are using UFW the first step is to set this rule:
```
1:65535/tcp                ALLOW IN    127.0.0.1
1:65535/udp                ALLOW IN    127.0.0.1
```to allow all localhost communication. next, if it's a network printer, add these rules:
```
515,631,8611,9100/tcp      ALLOW IN    192.168.0.9
515,631,8611,9100/udp      ALLOW IN    192.168.0.9
```where 192.168.0.9 is your network printer
lastly, if your printer uses mDNS then add this rule:
```
224.0.0.251                ALLOW IN    192.168.0.0/16
```or your UFW log will be flooded with block events
obviously replace 192.168.0.0/16 with your network

---

### Post by gunterkoenigsmann on 2012-10-28
ubuntu 12.10 does no more seem to have to have a system-config-printer command ;-(

---

### Post by SWRP on 2013-08-27
Thank god I found your post - I'm now network configured to my printer.
Thats after hours of trying to find how to fix my problem.
Thankyou again gilgongo

---

