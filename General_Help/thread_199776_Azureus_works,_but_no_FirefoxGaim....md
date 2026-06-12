---
title: "Azureus works, but no Firefox/Gaim..."
date: 2006-06-19
forum: General Help
---

### Post by metro.tramp on 2006-06-19
I had my xubuntu dapper box running fine on the internet, using any network/internet software without problems.

But I've just bought a new broadband connection and so am using a new router, as the previous one doesn't work with ASDL-2. 

Azureus runs fine (and downloads at lovely speed :D  ), and filesharing works fine with samba, but neither Firefox nor Gaim can connect to the internet. I also tried an ```
apt-get update
``` but it couldnt connect to the servers.

My housemate's WinXP box connects to the internet fine (as this post proves), so i'm guessing this all has something to do with the settings on my xubuntu box, but i have no idea how to change them to work...

Which is where you come in! ;) 

What do i do?

---

### Post by metro.tramp on 2006-06-20
Any ideas? :confused:

---

### Post by truoc444 on 2006-06-20
can you get to any websites in firefox using the ip address instead of the words?  can you ping ip addresses?  sounds to me like a dns problem.

---

### Post by metro.tramp on 2006-06-20
Oooh. yeah.
IP addresses seem to work.

So how do i sort out my DNS stuff?

Doesnt seem to a be a problem at the isp end of things, as normal adds are working for WinXP and OSX boxes.. 

What do i need to fiddle with?

---

### Post by SDREnate on 2006-06-20
I'm having the same troubles with our new Adelphia cable setup. We're using a Linksys wireless G router, but I'm hardwired to it. Azureus will work, sometimes AIM will too, but I don't get any internet. I'll hit the reset button on the router, then everything will be fine for awhile before it stops working again. I think I may have to reconfigure the router settings. I have a feeling the person that set it up did something wrong.

---

### Post by ayoli on 2006-06-20
two way to add DNS servers:
1) go into menu Administration > Network then pick  the DNS tab and add a DNS   server (ie: the DNS servers IP from your ISP)

2) in a terminal:
```
gksudo gedit /etc/resolv.conf
```
and add a line like this:
```
nameserver xxx.xxx.xxx.xxx
```
where xxx.xxx.xxx.xxx is the DNS server IP from your ISP

cheers.

---

### Post by metro.tramp on 2006-06-20
Works for me :D 

Thanks!

---

