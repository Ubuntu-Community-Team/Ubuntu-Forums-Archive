---
title: "Can't connect to internet"
date: 2006-03-25
forum: General Help
---

### Post by bgravengood on 2006-03-25
Like many others, I don't seem to be able to connect to the internet, or better, maybe, I'm not able to log in. As far as I know, I've confìgured everything correctly, if I try to ping something I get a positive response. What could be the problem? With Simply Mepis I had to give my username and password, but I can't find this option any where in Ubunto. Thanks in advance for your help.

Bill

---

### Post by tseliot on 2006-03-25
What do you mean when you say you're not able to log in?

Can you see the graphical login manager (GDM)?

---

### Post by bgravengood on 2006-03-26
Sorry, I'm probably not explaining myself very well. When I connect with the internet with Windows, and it seems like it was the same with the other versions of Linux I've used in the past, I have to give my username and password, I don't mean "log in" to the session. I really don't have any idea if this is the problem, it just seemed strange to me. Anyway, this is my ip configuration under windows:

C:\>ipconfig -all

Configurazione IP di Windows

        Nome host . . . . . . . . . . . . . . : bill-qti56loeoc
        Suffisso DNS primario  . . . . . . .  :
        Tipo nodo . . . . . . . . .  : Sconosciuto
        Routing IP abilitato. . . . . . . . . : No
        Proxy WINS abilitato . . . . . . . .  : No

Scheda Ethernet Connessione alla rete locale (LAN):

        Suffisso DNS specifico per connessione:
        Descrizione . . . . . . . . . . . . . : Intel(R) PRO/100 VE Network Conn
ection
        Indirizzo fisico. . . . . . . . . . . : 00-02-B3-20-37-16
        DHCP abilitato. . . . . . . . . . . . : Sì
        Configurazione automatica abilitata   : Sì
        Indirizzo IP. . . . . . . . . . . . . : 192.168.1.21
        Subnet mask . . . . . . . . . . . . . : 255.255.255.224
        Gateway predefinito . . . . . . . . . : 192.168.1.1
        Server DHCP . . . . . . . . . . . . . : 192.168.1.1
        Server DNS . . . . . . . . . . . . .  : 192.168.1.1
        Lease ottenuto. . . . . . . . . . . . : venerdì 24 marzo 2006 23.56.39
        Scadenza lease . . . . . . . . . . .  : sabato 25 marzo 2006 23.56.39

 I've tried to fill in all the fields under network configuration, I've probably just made a mistake somewhere, but since this is the first time I've had to configure an adsl connection manually, I really don't know exactly what I'm doing. Thanks for your help. 

Bill

---

### Post by Viorus on 2006-03-26
if i understand you right you have a modem where you have to login before connection to the internet? (where you here those connection sounds from you modem):confused:

---

### Post by bgravengood on 2006-03-26
No, sorry. Well, I live in Italy, I don't know if it's different here, but when you connect with the internet, even with adsl, you have to log into the service provider with a username and password, just like with a dial up connection. It's just that, with Ubutu, I've configured the network connection as well as I could - i.e. I wrote in the ip adress, the subnet mask and gateway numbers etc., but I still can't connect. I thought it was strange that I was never asked for my username and password to log into the service provider. But maybe that has nothing to do with anything, I don't know, I only know that I've tried everything that I can think of, and I can't connect to any sites. I pasted my ip address into the browser's address window, and I was connected with a Telecom site which gave me information about my account, 
so I know the O.S. sees my connection, I just don't seem to be able to go anywhere. If I try to connect with [www.google.com](www.google.com), for example, it tells me to configure my network under "network configurations" or whatever its called (I can't remember now since I'm sending you this from Windows). I realize that it's probably just some simple thing that I'm missing, but for the life of me, I can't figure out what it is. I've spent hours at this, and as much as I like Ubuntu, I'm thinking to just go back to a more user friendly version of Linux like Mandriva or something... However, if you can help me figure out what I've done wrong, I'd appreciate it. 
Bill

---

### Post by LordMerlin on 2006-03-27
Well, give this a shot....

It sounds like you need to setup a PPPOE connection, thus
First, install pppoeconf (apt-get install pppoeconf)

And then simply run it :)

It's going to ask you for the username & password, which will then create an interface ppp0

hth

---

