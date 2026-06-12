---
title: "Network Issues on WAN"
date: 2006-04-14
forum: General Help
---

### Post by jonnymccullagh on 2006-04-14
I am able to browse the web etc but I am having a few other issues. I am on a corporate network on a subnet e.g. 192.168.8.*

I am able to ping addresses in my own subnet only (inc my proxy) - I cannot ping to addresses on other networks on my WAN which I should be able to.

Is something else I should be doing for network settings?

Thanks,
jonny

---

### Post by cwaldbieser on 2006-04-16
[QUOTE=jonnymccullagh]I am able to browse the web etc but I am having a few other issues. I am on a corporate network on a subnet e.g. 192.168.8.*

I am able to ping addresses in my own subnet only (inc my proxy) - I cannot ping to addresses on other networks on my WAN which I should be able to.

Is something else I should be doing for network settings?

Thanks,
jonny[/QUOTE]
Sounds like your routing table is not correctly configured.  Try making sure your default gateway is set to a router that knows how to talk to the other subnets.  If that doesn't help, try posting the output of "route" from the terminal and maybe someone can pick up on the problem.

---

### Post by jonnymccullagh on 2006-04-24
route shows the following:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth0

Now, my gateway should be 192.168.8.250
Next I tried going to K->System Settings->Network Settings
My LAN card shows up on Network Interfaces with the IP address but when I click the 'Routes' tab, the box for Default Gateway IP Address appears empty. I tried entering my gateway address and applied. Then I closed and reopened Network Settings and the Default Gateway box is empty again.

Could this be my problem? How do I manually set the Gateway address?
thanks for your help cwaldbieser,
jonny

---

### Post by jonnymccullagh on 2006-05-05
I discovered my problem (this may help others) but I still have another problem. I can fix my gateway problem but only temporarily - Can someone tell me how to get it to stick or even if can can run this command automatically on boot (and if so how)?

There seems to be a bug in kubuntu (Breezy 5.10) in holding the Gateway address in the Network Settings. When typing ftp or telnet at the command line I got an error messgae of: Network unreachable
I was still able to browse the web using Firefox etc but I was unable to use FTP or Krdc Remote Desktop (I also needed to apt-get install rdesktop before attempting this).
I was unable to get outside my own work subnet on our WAN. 
Apparently this problem does not occur on Ubuntu/Gnome so it confirms that Kubuntu is more of a challenge at getting up and running but hopefully these issues will be sorted in Dapper.

This presented several critical problems to me but I found an answer on the web after struggling for a week or two with it. The answer was here:
[http://www.ubuntuforums.org/archive/index.php/t-25915.html](http://www.ubuntuforums.org/archive/index.php/t-25915.html)

and all I had to do was type at the command line:
sudo route add default gw xxx.xxx.xxx.xxx

The option of editing /etc/network/interfaces did not work for me.

Any help is appreciated as I am currently moved over to Gnome so I can get my work done but I do not like it much :-(
thanks,
jonny

---

