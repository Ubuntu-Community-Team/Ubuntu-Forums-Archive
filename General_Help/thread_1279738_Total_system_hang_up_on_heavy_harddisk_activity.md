---
title: "Total system hang up on heavy harddisk activity"
date: 2009-10-01
forum: General Help
---

### Post by Gernot74 on 2009-10-01
Hello,

I have a problem that I am unable to solve myself.

I am running an Ubuntu Jaunty x86 64bit system.

Mainboard: Kontron 986LCD/mITX with 3x Gigabit-LAN
Harddisks: 1x 40 GB IDE 2.5" system harddisk (MASTER on onboard IDE controller)
                2x 1 GB S-ATA 3.5" as software RAID-1 for Data

When I move large amounts of data (e. g. a CD image) over LAN to the harddisk, the system freezes after some time during the data transfer.

It does not matter wether I transfer the data to the RAID array or to the system harddisk.

I then tried to test the harddisk alone by using bonnie++. That also froze the system.
A fsck on the raid array resulted again in the whole system freezing.

When I say the system is freezing, I mean the whole system, not just harddisk operations. No data is passing through the network adapters anymore (the machine is running as router between network segments and no traffic is routed anymore), I cannot login at the console, I cannot login remotely via ssh.

Logfiles have nothing in either, that is related to that problem.


Any idea how to solve that problem or at least what to test is highly welcome.
I am absolutely clueless what is going wrong.

Thanks,
Gernot

---

### Post by winz on 2009-11-05
Same problem here, AMD Athlon XP, 32 bit. Sometimes, it works fine for weeks. Then it starts hanging up every time I try to copy a movie over the network. So, either a heavy hard drive activity, or network activity. The pc just stops responding to pings.

But there's a workaround that brings it back to life: insert or reattach any USB device, be it a flash stick or a 3g modem. Works every time.

Dmesg is absolutely clear:

Nov  5 23:31:16 server kernel: [  889.137833] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
(... That's where we stop responding. And then - USB device attached ...)
Nov  5 23:53:10 server kernel: [ 1865.732055] usb 1-6: new high speed USB device using ehci_hcd and address 4

Very strange issue. I was hoping, upgrading to 9.10 would help, but so far the same.

---

### Post by dcstar on 2009-11-05
> **winz said:**
> Same problem here, AMD Athlon XP, 32 bit. Sometimes, it works fine for weeks. Then it starts hanging up every time I try to copy a movie over the network. So, either a heavy hard drive activity, or network activity. The pc just stops responding to pings.
..........
Very strange issue. I was hoping, upgrading to 9.10 would help, but so far the same.

There are already many posts in the 64-bit forum on issues similar to this, some have workarounds.

---

### Post by winz on 2009-11-06
> **dcstar said:**
> There are already many posts in the 64-bit forum on issues similar to this, some have workarounds.

Thanks for your input, David.

I spent an hour this morning searching for such issues in the 64-bit forum. Most of them seem to relate to the nvidia driver. I still can't see any workaround there..

Also, my system is 32 bit, not 64. It freezes only on high network activity, not hard disk. I tried to copy big files from one folder to another - everything is fine. But if I try to copy it over the network, it usually freezes.

This PC is a headless ubuntu-server 9.10, so there's no nvidia driver loaded.

Again, inserting any USB device always makes it unfreeze.

I tried 3 different PCI ethernet cards in all PCI slots. All of them were RTL8139, though. Today is worse than ever. It stops responding to pings like every half an hour. Copying files over samba, http, ftp, sftp - all lead to the same result. And if I put two ethernet cards, and switch between them during the freeze, the second eth-card isn't trying to get an IP address via DHCP. Sometimes, it just hangs by itself, in the middle of the night. Maybe, some a bit more higher network activity was going then. Extremely frustrating issue.

**UPDATE**: it looks, like my case is different than the original case of Gernot. A friend of mine has the same issue, and he says that he's able to do "service network restart" during the freeze. I couldn't do that, as I don't have any keyboard/monitor connected to the server, but I will try tomorrow and update.

**UPDATE 2**: OK, adding acpi=off to menu.lst in the current kernel line **SOLVED** the problem for me! The interesting thing is, that the network connection hanged up only on high outgoing network activity, be it uploading to another pc or just being a NAT router for other PCs. Hope, this helps anybody!

---

### Post by aquabubble on 2009-12-18
Hi,
 
Similarly, I have a 9.10 server (though with a keyboard and monitor) which was hanging on copying large files across the network (via samba). The copy process would hang and then the my server would become unresponsive - but only to inbound network access; a local shell was perfectly responsive and outbound network was fine! I happened upon the fact that it would resume normal behaviour when unplugging and replugging the network cable, then I saw this post; sudo /etc/init.d/networking restart also seemed to fix the problem though only temporarily - it would always eventually hang (with nothing in any log).
 
However, when I added acpi=off to the kernel startup parameters, the hanging went away! I'm very grateful for this post, but how random is this problem?!

---

### Post by winz on 2009-12-18
After upgrade to 2.6.31-16 all hangs went away even without any acpi tweaks. If any of you are experiencing similar hangs, I highly recommend upgrading to the latest kernel in ubuntu repos.

---

