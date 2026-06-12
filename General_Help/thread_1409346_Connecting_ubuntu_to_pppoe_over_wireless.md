---
title: "Connecting ubuntu to pppoe over wireless"
date: 2010-02-17
forum: General Help
---

### Post by vishnu93 on 2010-02-17
Hello,
         I am new in linux. I have a broadband (PPPoE) connection which I want to access through wireless. I was able to do it by using sudo pppoeconf. The connection was made through wlan0. But when I restarted my Laptop something went wrong. in 'network manager applet' under 'wireless  networks', instead of available networks, 'Device not managed' is written. I tried uninstalling the network manager and reinstalling it, editing interfaces file of /etc/networks/, etc. Finally I had to reinstall my Ubuntu.But same thing happend when I tried to connect again. I use ubuntu9.10 in  my acer aspire 3680. I made clean install. Now I have only ubuntu in it. So I need the solution fast.
Please help Me...

---

### Post by vishnu93 on 2010-02-18
I need help. Please.....

I want to use ubuntu but my only problem is I can't access internet

---

### Post by JmanJulian on 2011-06-26
This is an old thread but the solution may be useful to someone. So the problem with the pppoeconf after reboot is that it puts a definition of you're wireless card in the network interfaces file and that conflicts with network manager witch is a very limited and still lacking features like pppoe over wifi. To solve the problem open "/etc/network/interfaces" file with any text editor end delete all lines containing wlan0 (you can use command "sudo gedit /etc/network/interfaces"). After youre done it should contain only this:

auto lo
iface lo inet loopback

iface dsl-provider inet ppp
provider dsl-provider

Now after you restart you can use Network-Manager to connect to a wifi network and you can activate pppoe link with the command "sudo pon dsl-provider" and shut it down with "sudo poff".

---

