---
title: "internet only works for the first website"
date: 2006-06-29
forum: General Help
---

### Post by guine on 2006-06-29
I just did a fresh install of dapper because Ive destroyed every other operating system on my computer over the weekend(including dapper once already) and when I boot Im able to load one website, it doesnt seem to matter what website it is, and then I completely lose internet access.  I know my hardware works fine because im booting from the live cd right now and everythings working fine, and my internet worked fine on my last dapper install until firefox went crazy.  My ethernet card is showing up as enabled and appears to have been installed fine.  Any clues on how to fix this?  Thanks

---

### Post by Arisna on 2006-06-29
Okay, let's check out a few possibilities here.  Try out these steps on the installation that's giving you problems.  Do it after you have visited that first website, and make it a website other than Google.

First, I'm wondering whether the problem might be with the browser you are using.  Do you have another browser program available to try, perhaps Konqueror?  (I see you're a Kubuntu user, and I take it from your post that you normally use Firefox)

If that doesn't change things, it's time to check for outright connectivity problems.  Open up a Konsole and enter the following:

```
ping -c 3 64.233.167.99
```

That will attempt to ping one of Google's servers.  If you get a reply all three times, the problem is not connectivity.

If that works, then let's see if this is a problem with DNS.  In the Konsole, enter this:

```
ping -c 3 google.com
```

You should receive bytes back from Google, not an error message that says "Unknown host google.com".

Give it a shot, and post your results so that we may better assist you. :KS

EDIT:  One more thing.  Just in case, enter the command "dmesg" (leave off the quotes) in that Konsole window at the end if you do not conclude anything from the above tests.  This command prints information about hardware-software interaction on your system.  See if you're getting any nasty looking error messages toward the end of the output.

---

### Post by guine on 2006-06-29
Right now Im using ubuntu so I dont have konqueror to use(Im normally in kde and use firefox though) but I havent been able to connect with gaim or through synaptic.  When I tried ping -c 3 64.233.267.99 I got this back:
```
Ping 64.233.167.99 (64.233.167.99) 56(84) bytes of data.
From 192.168.1.45 icmp_seq=1 Destination Host Unreachable
From 192.168.1.45 icmp_seq=2 Destination Host Unreachable
From 192.168.1.45 icmp_seq=3 Destination Host Unreachable

--- 64.233.167.99 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet, loss, time 1999ms
,pipe 3
```

I checked dmesg and these were the only things that I saw referring to my network card:
```
eth0: Davicom DM9102/DM9102A rev 49 at 0001d800, 00:08:A1:0C:E9:79, IRQ 209.
eht0: Setting full-duplex based on MII#1 link partner capability of 41e1.
eth0: no IPv6 routers present
```
There were also several messages that showed:
```
NET: Registered protocol family ##
```
incase that means anything.  Hope this provides some more info.

---

### Post by Arisna on 2006-06-29
Since other applications are also not working, the problem isn't the browser.  Although you were not able to ping the IP address I posted, it does not look like the problem is entirely with connectivity, since something else on your network responded to the request.  More stuff to check:

Navigate to System > Administration > Networking > "DNS" Tab in the problem installation.  See if there is anything in "Search Domains."  I ended up with some random stuff in there when I did my installation that crippled my Internet access.

Also, I should have asked for this before, but go in a Terminal and get the output of "ifconfig".  That will at least tell us if you do indeed have a working LAN connection.

---

### Post by guine on 2006-06-29
In search domains I have "myhome.westell.com", is this something that should be there or should I just delete that.
My output from ifconfig is:
```
eth0      Link encap:Ethernet  HWaddr 00:08:A1:0C:E9:79
inet addr:192.168.1.45 Bcast:255:255:255:255 Mask:255:255:255.0
inet6 addr: fe80::208:alff:fe0c:e979/64 Scope:Link
UP BROADCAST MILTICAST MTU:1500 Metric:1
RX packets:33 errors:3458 dropped:0 overruns:0 frame:0
TX packets:15 errors:1 dropped:0 overruns:0 carrier:1
collisions:0 txqueuelen:1000
RX bytes:3171 (3.0 KiB) TX bytes:1453 (1.4 KiB)
Interrupt:201 Base address:0xd800

lo       Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:13 errors:0 dropped:0 overruns:0 frame:0
TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RXbytes:976 (976.0 b)  TX bytes:976 (976.0 b)
```
If you think this might just be something that went wrong during the install and would be easier to just do a fresh install and hope it works better thats not a problem for me because I have nothing on this harddrive.

---

### Post by Arisna on 2006-06-29
I suggest deleting the myhome.westell.com thing and seeing what that does.  While you're at it, make sure you can ping 192.168.1.1, which should be your router.

---

### Post by guine on 2006-06-29
I gave deleting myhome.westell.com thing a try but that didnt do anything(it also returns when I reboot my computer).  When trying to ping 192.168.1.1 I got the same problem as before.  Also, Im no longer able to reach any webpages as I was before when I could reach one, but Im guessing that being able to reach one webpage earlier was a fluke.

---

### Post by Arisna on 2006-06-29
Alright, let's try something a little different.  In the Networking config tool, go back and delete the myhome.westell.com entry under Search Domains again.  Now, click the "Hosts" tab.  Click on "Properties" for the entry 127.0.0.1.  Make note of what is in the Aliases box below the line with the IP address.  Now, change whatever is there to something like this:

```
your_preferred_hostname.your_preferred_domainname
localhost.localdomain
your_preferred_hostname
localhost
```

Of course, change the "preferred" things to whatever invented hostname and domainname you want to use for the machine.  You may even want to leave those entries out and only have localhost.localdomain and localhost.  Things will not work out well if your machine thinks it is on someone else's network, according to what I've just read on the Internet.

---

### Post by guine on 2006-07-01
I gave the changing the 127.0.0.1 alias thing a try but that didnt have an effect.  I decided to go ahead and try a reinstallation of dapper to see if something just went wrong the last time but my internet still doesnt work properly.  It appears that the being able to visit one webpage thing was not a fluke and I am still able to do one thing on the internet before losing it, whether it is visiting a website, pinging another computer, or pinging my own computer from a different computer.  I am able to do any of these if its the first thing I try to do on the internet but once I do any of them the internet goes out.
I was talking to my brother and he was thinking that I may need to do something with my dhclient so we tried checking a bunch of things with dhcp and dhclient.  Heres the things that we checked incase you see something wrong that we missed.  
I originally had this in /var/lib/dhcp3/
```
dhclient.ath0.leases  dhclient.eth2.leases  dhclient.wlan0.leases  dhclient.eth1.leases  dhclient.leases
```
after a reboot, dhclient.eth0.leases was also added to the list but having eth0 show up there didnt effect how the internet was working.
My /etc/dhcp3/dhclient.conf is same as it is on another computer using dapper that has working internet.
This is what I have in /var/lib/dhcp3/dhclient.eth0.leases
```
Lease {
  interface "eth0";
  fixed-address 192.168.1.45
  option subnet-mask 255.255.255.0
  option routers 192.168.1.1;
  option dhcp-lease-time 86400;
  option dhcp-message-type 5;
  option domain-names-servers 192.168.1.1, 192.168.1.1;
  option dhcp-server-identifier 192.168.1.1;
  option broadcast -address 255.255.255.255;
  option domain-name "myhome.westell.com:'
  renew 6 2006/7/1 15:36:08;
  rebind 0 2006/7/2 01:12:57
  expire 0 2006/7/2 04:12:27;
}
```
From this it looked like everything is getting setup all nice and correct, but as soon as I try to do something with the internet with my computer, the router decides it doesn't want it connected, and it doens't work any more.  I tried pulling the power on the router and plugging it back in to see if that would reset the router and fix the problem but that only had the effect of restarting my computer, I was able to do one thing with the internet before losing it.  Any clues on anything else to try?

---

