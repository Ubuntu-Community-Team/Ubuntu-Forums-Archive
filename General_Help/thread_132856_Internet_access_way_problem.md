---
title: "Internet access way problem"
date: 2006-02-19
forum: General Help
---

### Post by malic on 2006-02-19
I tried lots of linux distros and had a common problem which is network problem. For example after installing ubuntu (or others), firefox does not work properly in other words it can not explore any web pages. The only way of opening web pages is changing the default setting of "network.dns.disableIPv6" as true. I type "about:config" into the adress bar of firefox, then press enter and then type network into the filter box, finally find "network.dns.disableIPv6" and change its configuration value as true by right clicking on "network.dns.disableIPv6" and direct clicking on "toggle". After these steps firefox explores all web pages, but my problems continues with other properties such as update and gaim. I can not update any linux distro and i can not enter gaim. It says always that "Connection could not established."
Now, how can i solve my problems? Thanks... :)

---

### Post by bscbrit on 2006-02-19
Try this:

[https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28ipv6%29](https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28ipv6%29)

---

### Post by malic on 2006-02-19
[QUOTE=bscbrit]Try this:

[https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28ipv6%29](https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28ipv6%29)[/QUOTE]
Thanks for your help. I disabled ipv6 but my gaim and update problem was not solved. Now firefox can explore web pages without changing ipv6 configuration as true. I could not understant why gaim does not work. I type my screen name and password correctly but gaim can not connect to the related server.

---

### Post by bscbrit on 2006-02-19
How do you connect to the internet - do you have a modem/router and, if so, does it pass the appropriate ports for Gaim etc?  Do you have a firewall?

---

### Post by malic on 2006-02-19
I access the internet by using DSL Router with eternet ports. I only installed ubuntu i do not know whether ubuntu has firewall or not. But My DSL Modem has firewall. It writes on its package box.

---

### Post by bscbrit on 2006-02-19
Ubuntu does not have a firewall installed by default so, unless you installed one, we can ignore that.  What make and model of DSL router do you have?

---

### Post by malic on 2006-02-19
[IMG]http://www.mavibilgisayar.com/urunresimler/faxmodem/CREATIVE_8015U.jpg[/IMG]
**CREATIVE 8015U Modem**
> Modem Türü	 ADSL
Arabirim	 USB ve Ethernet
Garanti Süresi	 36 Ay
Di&#287;er Özellikler:

    8 Mbps down-stream ve 1 Mbps up-stream
    USB ve EThernet arayüzü
    ADSL2/2+ deste&#287;i
    Dahili Router
    Web tabanl&#305; GUI yönetimi
    Güncellenebilir Firmware 

    1X RJ-11 Telefon Soketi (DSL giri&#351;i)
    1X RJ-11 Telefon Socketi (telefon hatt&#305; giri&#351;i) 
    1X RJ-45 10/100Base-T Ethernet giri&#351;i 
    1X USB Portu

    Fiziksel Özellikler
    Uzunluk: 145mm
    Geni&#351;lik: 125mm
    Yükseklik: 30mm
    A&#287;&#305;rl&#305;k: 220g

    Teknik Özellikler
    ANSI T1.413 Issue 2
    ITU-T G.992.1(G.dmt)
    ITU-T G.992.2(G.lite)
    ITU-T G.992.3, G.992.4 (ADSL2)
    ITU-T G.992.5(ADSL2+)
    Encapsulation Deste&#287;i

    RFC2684 Bridge and Routed LLC and VC Mux
    RFC2364 PPPoA
    RFC2516 PPPoE
    Routing Protokol

    Dynamic Internet Protokol (IP) routing
    Network Address Translation (NAT)
    Dynamic Host Configuration Protocol (DHCP) Server / Client
    Port Mapping / Forwarding
    Demilitarized Zone (DMZ)
    Management Support

    NAT for basic Firewall
    Packet Filtering Firewall
    Stateful Packet Inspection 

---

### Post by malic on 2006-02-20
Hi... :) What do i have to do for updating ubuntu and entering gaim?

---

### Post by bscbrit on 2006-02-20
Malic, I do not know.  But I am looking on Google to try and find some answers.  Perhaps someone else reading this knows how to solve the Gaim problem?

---

### Post by malic on 2006-02-20
Bscbrit, thanks for helping me :) I think this problem will make me an expert on network technology.:p  I tried lots of ways and learned many many things about network protocols. :)

---

