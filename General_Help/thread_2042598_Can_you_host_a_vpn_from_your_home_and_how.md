---
title: "Can you host a vpn from your home? and how?"
date: 2012-08-14
forum: General Help
---

### Post by KIRON127 on 2012-08-14
Hi guys, i have been searching and searching and i don't know if im just searching the wrong thing or if im just missing it. But is there a way to host a vpn at your house so that you can connect to it from a laptop somewhere like a coffee shop or something that has a web filter so that you can bypass it? I have a spare laptop running win7/ubuntu 12.04 and would like to host a vpn from that so i can connect to it from my phone/laptop when at places with a web filter. If you guys can point me in the right direction that would be awesome.

p.s. ive been reading about it and i don't want to buy server space or pay for a vpn on the internet somewhere, i would like to host my own so that i don't have to pay X amount of dollars a month to use it.

---

### Post by QIII on 2012-08-15
I'd start [here](https://help.ubuntu.com/community/OpenVPN) and read through it.  At the bottom are some more links.

---

### Post by KIRON127 on 2012-08-15
I have no idea what im looking at there haha. Im not necessarily new to ubuntu/linux but im no wizard at the terminal. i don't take it there is an easier way to do this is there?

---

### Post by Zukaro on 2012-08-15
Yes; I've actually managed to sorta get a VPN working (still working on it though as it doesn't seem to be doing what I want to do).

As long as your computer is on the VPN should automatically run (like, on the computer you're using as a server).  You wont need to buy a server or anything you just need a spare computer lying around to run the VPN (I'm using a 10+ year old computer for my VPN :P).

Here's some info: [http://www.ubuntugeek.com/howto-configure-pptp-vpn-in-ubuntu-intrepid-and-jaunty.html](http://www.ubuntugeek.com/howto-configure-pptp-vpn-in-ubuntu-intrepid-and-jaunty.html)
(for an older version of Ubuntu however)


Also, if you have a Linksys router running DD-WRT you can run a VPN through that rather than needing a computer for it (you'll need to look on the DD-WRT website for info on that however).

There's not much I can do to help however, as I don't really know what I'm doing, but I though I'd help try pointing you in the right direction.

I only know of two types of VPN, PPTP, and L2TP.  Look up something like setting up a PPTP or L2TP VPN on Ubuntu on Google and you should find some stuff (PPTP is the easiest to set up I hear, however, I've heard it's not as secure as the other ones).


Another thing you could do is SSH tunneling (however, I hear it's better to use a VPN).  Something I tested out today was 'ssh ipaddresshere -l zukaro -X firefox' (replace ipaddresshere with your public IP address and zukaro with your username; you can replace firefox with any application you want to run through the tunnel), what that did was opened up Firefox on the computer I was connecting to with SSH and opened a window on my other computer.  From another computer connected to the server with SSH I was able to close the window on my laptop (since I could go into top and then kill the program).

If all you need is a secure web browser an SSH tunnel might be easier to use than a VPN.

---

