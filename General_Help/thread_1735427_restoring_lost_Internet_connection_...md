---
title: "restoring lost Internet connection .."
date: 2011-04-21
forum: General Help
---

### Post by dragonfly41 on 2011-04-21
I've got Vista and ubuntu 10.10 as my two operating systems on separate partitions.  Grub dual boot.

Internet connection has worked fine so far on both OS.

Today I accepted a pop-up prompt in ubuntu to upgrade packages.

Now Ive got no Internet connection on ubuntu but I still have Internet connection on Vista on same laptop.   Same physical configuration.

I've run quickly through ubuntu system testing and this confirms no Internet connection.

What process do I have to go through to restore Internet connection on ubuntu?

If (worst case) I do have to reinstall ubuntu over the existing installation will installed packages and data be retained?

I've noticed that the ubuntu startup splash appears different from the usual ubuntu startup splash and my suspicion is that something in today's update of packages has screwed up some networking configuration.

---

### Post by dino99 on 2011-04-21
look at menu: system admin network

is it with wifi ? which chipset ?

sudo apt-get update
sudo apt-get install -a
sudo dpkg-reconfigure network-manager

---

### Post by dragonfly41 on 2011-04-21
well I'm switching between ubuntu and Vista to use Firefox ..

> is it with wifi ? which chipset ?

I have no wi-fi (I use cable) and I'm discounting any hardware issues (chipset etc.) since Internet has worked fine before (packages upgrade) and is working now (in Vista) as I post this reply.

in devices
IPv6 and IPv4

in netsat

tcp    127.0.0.1    631    listen
tcp    127.0.0.1    3306  listen
tcp6  ::               80      listen
tcp6  ::1             631    listen

> sudo apt-get update

tried that .. but of course it requires Internet connection and I saw a stream of 'failed to fetch' referring to packages not downloaded

> sudo apt-get install -a

the argument 'a' was not recognised

checked with man install and I don't see '-a' as an argument ??

> sudo dpkg-reconfigure network-manage

network-manager is broken or not fully installed

Thanks anyway.

---

### Post by dragonfly41 on 2011-04-21
I read another thread and looked at

/var/lib/NetworkManager/NetworkManager.state

but it seems o.k.

```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```

---

### Post by nothingspecial on 2011-04-21
Did you get a new kernel?

If so, restart and you should get options like this
2.6.38-7-generic
2.6.38-7-generic(recovery mode)
2.6.38-8-generic
2.6.38-8-generic(recovery mode)

Boot into the lower number, in my example with the 7 at the end.

---

### Post by dragonfly41 on 2011-04-21
I've never been sure what these different Grub boot options were ..

I have 
[COLOR=Blue]
2.6.35-generic
2.6.35-generic (recovery mode)
2.6.22-generic
2.6.22-generic (recovery mode)
memory test (86+)
memory test
Microsoft Vista .. Microsoft Vista boot point
extended XP .. Dell recovery point[/COLOR]

I've usually just selected the first option (which still gives no Internet connection)

**But** I tried the third option 2.6.22-generic and this gives Internet connection.   Thanks.

[EDIT] Just to add there was a stream of errors .. media errors .. shown in console before ubuntu started up 



Why are there two shell's in the Grub boot?


However having now tried a recovery in an effort to restore Internet I've lost some system files and applications (jEdit for example) and I'll probably setup now to have separate / partition and /home partition.

---

### Post by nothingspecial on 2011-04-22
Drivers (modules) for your hardware are included in the kernel. Sometimes when you get a new one something breaks. That's why the old one is kept around. Keep booting that one until you get a new one. Also report that your wireless card doesn't work with 2.6.35-generic. That way, they might fix it in the next one.

---

### Post by yossell on 2011-04-22
@dragonfly41

As you know from the other thread, [http://ubuntuforums.org/showthread.php?t=1736079](http://ubuntuforums.org/showthread.php?t=1736079)
I suddenly lost my wired connection too. 

Old kernels were no better for me. Moreover, my other Ubuntu machine, a laptop, ALSO stopped being able to use the ethernet connection, although wireless connection was fine. Strangely too, running an old version of slitaz from CD, I could get a wireless connection.

Baffled, I dug up an old BT hub and BINGO it was working. My only guess is that the BT hub received some software upgrade and the methods that Ubuntu uses to connect to the internet are now broken. 

It would be interesting to know how slitaz connects, what it does differently from Ubuntu, in order to regain internet access. 

I don't know if this helps but would be interested in your thoughts.

---

### Post by dragonfly41 on 2011-04-22
did you try [https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)

which spikoley suggested .. that works fine for me.

uses different dns settings.

I couldn't get 

sudo dhcpd eth0   

to work for me either

if you run     **[COLOR=Blue]man udhcpd[/COLOR]**   there is a list of commands including udhcpd .. but this might be a red herring!

I think that some form of Internet sniffer utility would help but I don't know enough about innards of ubuntu network manager yet.

[COLOR=Blue]
[EDIT]

re: sniffers ..

some sniffers listed here ..

[http://www.ubuntugeek.com/network-traffic-analyzers-for-ubuntu-system.html](http://www.ubuntugeek.com/network-traffic-analyzers-for-ubuntu-system.html)

Go into Ubuntu Software Centre and try installing Wireshark[/COLOR]

---

### Post by yossell on 2011-04-22
I've just got it working.

I tried different DNS settings but it didn't work.

I think spikoley missed a letter: it should be 

sudo dhcpcd eth0

Unfortunately, I didn't have dhcpcd installed - but when I connected my old hub and found it worked, I quickly installed it. I then went back to my new hub, ran the command, and then pasted the IP number that the command outputted into the DHCP client ID box, under IPv4 Settings. This then restored my connection with the new hub, solving my problem.

---

