---
title: "Internet Connection Sharing Setup."
date: 2006-06-03
forum: General Help
---

### Post by Patrick-Ruff on 2006-06-03
hey all, anyone know how you would go about doing this? the main host computer is a windows comp, which is connected to the internet and all that, since I'm doing this with only a LAN cable, it gets kinda complicated, however I was able to pull it off when I had windows installed on my laptop, the 2 computers seem to be communicating fine, but how bout setting up the ICS? its set up on the windows computer, but I'm not entirely sure the Linux laptop is actually taking atvantage of this, is there any things I should do to make this possible?

---

### Post by PriceChild on 2006-06-03
I find the dhcp doesn't work AT ALL for me... the only way i got the internet shared from the linux box to my 360 was to sort out static ips all round.

You don't need to bridge connections in linux, but you WILL need to enable ICS in winows.

Pricey

---

### Post by Patrick-Ruff on 2006-06-03
I did do the ICS thing in windows, but it doesn't seem to be sharing the internet with the linux box.

---

### Post by Patrick-Ruff on 2006-06-03
ah its ok guys, figured it out, zone alarm was blocking it, does anyone know what service/application to let through so zone alarm doesn't block ICS?

---

### Post by shae on 2006-06-04
I actually have some experience with this problem.  I am on a simple AB network through a Windows XP Computer.  From what I understand about basic networking, only certain IP addresses are assigned by DHCP for local networks.  So, you could try placeing these ranges into your "Trusted" zone or w/e they call it these days.  Quite frankly I have checked out of careing for our Windows box letting my brother take care of it.  All I do is get in a few games now and then.  You could assign your computers static addresses on both host and client.  Then allowing just these two IPs should make it work.

---

