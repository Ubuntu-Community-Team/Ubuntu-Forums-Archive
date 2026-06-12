---
title: "howto  Automatically forward ports on my router"
date: 2009-07-17
forum: General Help
---

### Post by nikhilbhardwaj on 2009-07-17
i was having a lot of trouble with accessing my machine from the net
as i have a dynamic ip address
but with a lot of help from [t4thfavor]("http://ubuntuforums.org/member.php?u=230154") here at the forums
i was able to get it all started.

To forward a port i have to add a virtual server specifying the ports
but after i reboot my router it seems to forget my port associations
and each time i restart i must enter the info manually.

today i started my pc in winXP and when i opened my router admin page 192.168.1.1
on the list were 
#     PrivateIP       Prorocol     PrivatePort     PublicPort
1     192.168.1.x      TCP         25011            25011
2     192.168.1.x      UDP         25011            25011

initially i panicked
and thought someone had hacked my router and added these
but upon seeing tcp and udp in the protocols
i suspected that it may be utorrent and upon checking its ports found out that it was indeed the application.

now i would like to know 
how this can be done in linux
or is there a script that i can write
by which i can forward port 8080 to 8080 on my machine
and run it every time i start my computer or restart the router

---

### Post by nikhilbhardwaj on 2009-07-17
update

linux applications also create their virtual server entries
i started vuze after rebooting in to linux and there were two similar entries at port 17005

so all i need to figure out is a command that can forward port 8080
please help me with it:D

---

### Post by bodhi.zazen on 2009-07-17
Depends on your router and what you mean by rebooting it.

I rarely if ever reboot mine and if you are resetting it then that sounds as it is the problem.

I am not user you can issue a command from linux (or windows) to port forward. Most routers have a web interface you use to log into the router.

Perhaps if you told us what router you are using (manufacturer and model please).

---

### Post by hibliss on 2009-07-17
What utorrent did was use UPnP port mapping, which is also available in Linux bittorrent clients.

Now if you want to ssh or conect via VNC from across the web, you should first go to a site like No-IP or DyDNS and setup a free account. This solves the issue of the dynamic IP, as it will refresh hourly, or daily, or however you set it and you will be able to go to a domain instead of directly to the address. Example -- thisisyourdomain.no-ip.com:8080

Now the next thing you should do is set your Ubuntu machine to a static address on your local network. After doing that, you can manually forward the port in your router and not have to worry about the machine's IP changing, and even after a reboot of the router (which as stated above should not often be needed), the settings for the port forwarding will still be there.

---

### Post by t4thfavor on 2009-07-17
He want's to upnp forward to a webserver I helped him setup the other day. I will give it a looksee to se if I an find an easy script.


[http://www.howtoforge.com/administrating-your-gateway-device-via-upnp](http://www.howtoforge.com/administrating-your-gateway-device-via-upnp)

If you need more info on this I will be monitoring the forums for a while. I just had my wisdon teeth pulled, and will be off my rocker for a few days.

---

### Post by nikhilbhardwaj on 2009-07-17
[hi ]("http://ubuntuforums.org/member.php?u=230154")[t4thfavor]("http://ubuntuforums.org/member.php?u=230154")
this is what i get when i try to run the script 
Can't locate Net/UPnP/Device.pm in @INC (@INC contains: /usr/lib/perl5/5.10.0/i486-linux-thread-multi /usr/lib/perl5/5.10.0 /usr/lib/perl5/site_perl/5.10.0/i486-linux-thread-multi /usr/lib/perl5/site_perl/5.10.0 /usr/lib/perl5/site_perl .) at portset.pl line 33.
BEGIN failed--compilation aborted at portset.pl line 33.

line 33 is 
use Net::UPnP: Device;

i'm not very familiar with perl
but this seems like an include statement

perhaps its not present on my system

sorry
should've read it more carefully
its mentioned how to get it

sudo apt-get install -y libnet-upnp-perl

i'll let you know how that goes

---

### Post by t4thfavor on 2009-07-17
Get the script from his blog, as the one mentioned on the howtoforge doesn't work for me.


I got it working on my router, leet me know if you cannot get yours going.

---

### Post by nikhilbhardwaj on 2009-07-18
hi again
i got the script from his blog at
[http://ubuntu.blogetery.com/2009/04/16/a-smart-router-administration-tool/](http://ubuntu.blogetery.com/2009/04/16/a-smart-router-administration-tool/)

but it doesn't seem to work
i run it as root and still it didn't get it to work

nikhil[myBin]$ sudo ./router.pl -a -e 8080 -I 192.168.1.3 -i 8080 -P TCP
Scanning for devices ...
nikhil[myBin]$ 

thats what happens
and there's no change in the router admin page nor can i access it otherwise.


another side issue
i changed my router's password 
but after i power it off
and then on the next time it reverts back to the defaults

---

