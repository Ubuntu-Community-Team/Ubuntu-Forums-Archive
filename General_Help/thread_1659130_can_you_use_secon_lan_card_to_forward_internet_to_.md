---
title: "can you use secon lan card to forward internet to a second computer?"
date: 2011-01-03
forum: General Help
---

### Post by 0949er on 2011-01-03
I have a computer who has a wireless card I use for my local network and Internet. I have a second network card on this computer (onboard lan card), that I would like to use to forward an Internet connection to a older-generation laptop computer. Is this possible?

Main Computer Connection to Internet:
Internet > Wireless Router > Computer A

Laptop Computer:
Computer A > Laptop (via cat5 cable connecting my main computer to the laptop)

---

### Post by Dans564 on 2011-01-03
yes, here is how [http://www.makeuseof.com/tag/how-to-easily-share-your-wireless-connection-in-ubuntu-9-10/](http://www.makeuseof.com/tag/how-to-easily-share-your-wireless-connection-in-ubuntu-9-10/)

---

### Post by 0949er on 2011-01-03
I have selected share the eth0 connection, however, when I plug the two computer together via an Ethernet cable, on the window machine I get a "network cable unplugged" error. What do I need to do to get the computers to realise they can see each other?

---

### Post by Dans564 on 2011-01-03
does your network manager have any other options such as auto eth1?

---

### Post by 0949er on 2011-01-03
Just eth0, And just to re-state:

the wireless card will share the Internet to eth0, which will share to the laptop

---

### Post by Dans564 on 2011-01-03
yep if u follow that tutorial your wireless Internet connection will be forwarded through and out the Ethernet cable and into your second computer

---

### Post by colin.p on 2011-01-03
If memory serves me correctly, to connect one computer directly to another, without going through a router, I think you need a cross-over cable and not a "typical" cat5. However, I could be totally wrong. It may be easier to connect to the wireless router, assuming of course it has the standard 4 ethernet ports.

---

### Post by Smart Viking on 2011-01-03
> **colin.p said:**
> If memory serves me correctly, to connect one computer directly to another, without going through a router, I think you need a cross-over cable and not a "typical" cat5. However, I could be totally wrong. It may be easier to connect to the wireless router, assuming of course it has the standard 4 ethernet ports.

Actually, it works both with an ethernet cable and a crossover cable, at least when i did it through the NetworkManager settings a few months ago.

---

### Post by Dans564 on 2011-01-03
I'm using a plain old Ethernet cable to feed my western digital TV live plus with Internet from my desktop using the tutorial I provided.

---

### Post by 0949er on 2011-01-04
Dan, as far as I can tell the directions say:

Open Network Connections > edit eth0 > IPv4 Settings > "share connection"

which I have done. I have restarted also.

However when I physically plug the computers togeather, I get a "network cable is unplugged" error on the windows machine. Now, I have tested the computer by connecting it directly to the router and it works fine, however, the router is in a very unusual place so using the computer from there is not a option. what am I doing wrong?

*edit*

is this because I am not using a "crossover" cable?

---

### Post by Yougo on 2011-01-04
have you set up your windows computer to get internet though a gateway connection? 

maybe i'm behind on my network know-how, but indeed back in my windows days, to have two computers make a network, you needed a crossed cable. i realise i haven't done this with linux computers, let alone a mixed OS network yet

if you then wanted one to share the internet, you'd have to setup both the host and the client.

---

