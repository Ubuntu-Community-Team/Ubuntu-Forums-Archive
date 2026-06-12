---
title: "Two strange situations"
date: 2010-06-22
forum: General Help
---

### Post by JKyleOKC on 2010-06-22
I've got two quite strange situations here, that may or may not be related:

1) Syslog shows single lines reading "--- MARK ---" regularly at 7, 27, and 47 minutes past the hour. The first, at 7 minutes, appears to happen every hour. The second is skipped about 1/3 of the time, and the third about 2/3 of the time, but I've not seen any other pattern to these entries. And **nothing** in crontab or anacrontab fits those times. Searching for the string "MARK" in every file on the disk shows that this string is part of syslogd itself, but I'd very much like to know what is triggering it at these regular intervals.

2) Three times now in the past five days the on-board network adapter that's my eth1 interface has locked itself up. Here's the start of the typical syslog report:
```
Jun 21 12:09:59 mehitabel kernel: [255343.344591] NETDEV WATCHDOG: eth1: transmit timed out
Jun 21 12:09:59 mehitabel kernel: [255343.344596] eth1: Got tx_timeout. irq: 00000000
Jun 21 12:09:59 mehitabel kernel: [255343.344598] eth1: Ring at 1f9ee000
Jun 21 12:09:59 mehitabel kernel: [255343.344599] eth1: Dumping tx registers
Jun 21 12:09:59 mehitabel kernel: [255343.344604]   0: 00000000 000000ff 00000003 015203ca 00000000 00000000 00000000 00000000
 ... register and ring dump, then ...
Jun 21 12:09:59 mehitabel kernel: [255343.888212] nv_stop_tx: TransmitterStatus remained busy<7>eth1: tx_timeout: dead entries!

```

All three events have been the same, with near-identical log data, and all three have happened within a few minutes past 12:00 noon local time, with nothing shown in any log that I've been able to find to indicate what was trying to transmit. It happened on Wednesday, on Friday, and today, but not on Saturday or Sunday (the machine was turned off on Thursday as I was out shopping, unsuccessfully, for a replacement network adapter that would fit into the box's PCI-e available slot).

This is what lspci shows about the adapter:```
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
```and here's what lshw shows:```
       description: Ethernet interface
       product: MCP61 Ethernet
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: eth1
       version: a2
       serial: 00:26:18:70:fb:c5
       size: 10000000
       capacity: 100000000
       width: 32 bits
       clock: 66MHz
       capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=half ip=66.143.22.33 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=10MB/s
```
 
Re-booting does not clear things up, but powering down and unplugging the power cable from the box for at least several minutes **does** restore operation.

I'm running Hardy 8.04.04 LTS, fully updated, and wondering whether any recent security updates might be involved. The box had been operating flawlessly since last October in 24/7 service until this happened. The regular timing suggests to me that it must be a software effect rather than a hardware failure, and the timing with respect to the first note above makes me suspect a connection of some sort, but I'm open to all suggestions.

---

### Post by JKyleOKC on 2010-06-24
bump

The noon-hour lockup happened again today. That's four days out of the past eight and always within a few minutes after noon. Today was at 12:09:59 when first detected in syslog, and the connection was working at 12:03 according to a previous iptables report...

---

### Post by JKyleOKC on 2010-06-28
and again yesterday (6/27) and today...

---

### Post by canadianwriterman on 2010-06-28
I don't know if your interface lockup is related, but I found this old post about MARK that may explain where it comes from. Seems it's a normal process.

[http://ubuntuforums.org/showthread.php?t=513850]("http://ubuntuforums.org/showthread.php?t=513850")

---

### Post by JKyleOKC on 2010-06-28
Thanks for the response!

I checked out the old thread and have modified the syslogd defaults file as it recommends. That will hopefully cut down on the clutter in the messages log.

Now if I could just find a solution for the network adapter problem, which is driving me batty. I've installed a PCI-express network card to replace the problematic adapter, and also have tried a USB-to-RJ45 adapter, but neither of them are recognized. The card is sometimes recognized, but goes dead after only a few minutes of operation; the USB gadget shows up in lsusb, and its driver is loaded, but it never creates the usb0 network interface. I could do without quite so very many learning opportunities :confused:

Again, thanks much!

---

### Post by canadianwriterman on 2010-06-29
I've done a bit of digging and came across other references to your problem. Seems related to something called the "forcedeth driver."

One forum suggested booting into a prior kernel to see if that helps. Another solution is beyond my technical abilities, but it is here:

[https://lists.linux-foundation.org/pipermail/bugme-new/2004-March/012338.html]("https://lists.linux-foundation.org/pipermail/bugme-new/2004-March/012338.html")

Try searching eth1: **tx_timeout: dead entries!** and read through the entries. Maybe a solution hidden there!

---

### Post by JKyleOKC on 2010-06-29
Tou've saved my sanity, I do believe!

The symptoms listed in the Google search results are exactly what I am seeing here. I've tried one of the suggested cures (adding options in modprobe's list) and we'll see if it does the trick. If not, there are several other things I found there to try.

Didn't try any prior kernels but did try booting the latest live CD (10.04) and it made no difference.

I gather from your handle that you're also a writer; what type of material do you do? I was first published nationally more than 60 years ago, and made my living with my typewriter for more than 50 of those years, doing mostly electronics technical articles but toward the end of that time was doing software-related tutorials. The full story is at [http://www.jimkyle.com]("http://www.jimkyle.com") if you're interested.

Once more, many many thanks for the effort!

---

### Post by canadianwriterman on 2010-07-01
Thanks for the link, Jim... I'll take a look. I was a journalist here in Canada for many years and am currently a marketing writer.

Glas I could be of assistance and that you found a solution!

---

