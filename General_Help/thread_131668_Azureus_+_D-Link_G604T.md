---
title: "Azureus + D-Link G604T"
date: 2006-02-16
forum: General Help
---

### Post by mr.p on 2006-02-16
After much fustration with trying to get this to work, I have decided to see if anyone has any suggestions on how to get this to working.

I have run the latest Azureus 2.3.0.6 and 2.4.0.0 both are doing the same thing, not downloading/uploading. It passes the port test fine and the port is definetly open TCP/UDP. I am using a D-Link G604T to share my ADSL to my network, I did have some trouble with the DNS for some reason with linux, it would let me use the router as my DNS address on my linux machines, however it worked fine on any Windows machine, I solved this by just put the actual internet DNS servers in the DNS fields.

:confused:

---

### Post by mr.p on 2006-02-16
Attach is a screen shot of the port test pass.

---

### Post by slux on 2006-02-17
I have the same router. You know it runs Linux out of the box and you can even get a shell on it or replace the firmware with another by a hobbyist? :)

Are you using NAT on it or is it functioning as a bridge? You might need to set the router to forward packets to the port you choose to the machine you want to run azureus on if you're using NAT... The test shouldn't really work in that case though... What kind of torrents have you tried? Try something that really, really should start dropping bits right away to be sure it's not just some slow to start torrents.

---

### Post by twigboy on 2006-02-17
Are you saying your using your router as a dns server to the internet?

---

### Post by dotdot on 2006-02-17
yes i had the same problem - however gnome-btdownload  works fine..

..I've tried alsorts - works fine in win - doesn't in ubu - pain eh ?

I'm using it as a router btw

anyone - have the same config and have a solution - i know it's going to be something easy (I have setup a rule on the 604 btw for the port i have configed in az - however still no joy..)

..

---

### Post by mr.p on 2006-02-17
[QUOTE=twigboy]Are you saying your using your router as a dns server to the internet?[/QUOTE]

Yes, that's the default setup, as it just forwards DNS from the ISP DNS servers it picks up on connection, however this does not work with linux (Ubuntu, as far as I have tested). So for the time being I have put my ISP DNS server IP address as the DNS servers in my DHCP settings and its working fine.

I have setup a virtual server for Azureus on the router (running in NAT mode) and it passes the test as you can see, I have even tried using just UPNP and that doesn't work.

By the way, bittornado works fine. :) However the interface is crap.

---

### Post by mr.p on 2006-02-17
Hrmm... I'm dumb... :rolleyes: 

When I upgrade to j2re-1.5 I forgot to actually change it... "sudo update-alternatives --java"

Thanks for your help guys. However, the DNS is still a small issue, that's got me stumpped.

---

### Post by slux on 2006-02-17
I suspect the DNS thing might be caused by a sloppy DNS proxying implementation which doesn't do everything right when camoing as a DNS server and causes Linux to discard it's replies. I've seen the same thing on another router.

I wouldn't really call it an issue since it just eliminates an unnecessary step in the query but I agree it would be nice to get the dhcp server to just give you the real dns straight away or at least have a good way to override the DHCP reply's DNSs from the network settings dialog.

---

