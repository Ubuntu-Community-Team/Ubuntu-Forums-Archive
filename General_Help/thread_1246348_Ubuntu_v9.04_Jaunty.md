---
title: "Ubuntu v9.04 Jaunty"
date: 2009-08-21
forum: General Help
---

### Post by ellis rowell on 2009-08-21
In the past, Ubuntu has been easy to install, reliable and a joy to use. With this latest version it seems to rate last in computer OS's (including Windoze). I have tried several times to install it on my Acer Aspire T120 Desktop, each time it has shown that it has connected to Eth0 but will not work with the router (3Com Office Connect - no problems with previous versions). It eventually freezes completely and has to be switched off to recover.

I have also tried Mint, version 5 OK, version 7 (Ubuntu v9.04 equivalent) has the same problems.

I shall have to continue using U v8.10 or v8.04 LTS. When they are no longer supported I shall have to subscribe to Bill Gates Pension Fund.

---

### Post by ajgreeny on 2009-08-21
Are you sure your CD is OK and not corrupt in any way?
9.04, in my opinion, is the best version of ubuntu so far, but it will depend to some extent on your hardware, and there were a few graphics cards, in particular that caused problems on installation.  I think that they have now largely been sorted out, however, so if you are not fully updated, perhaps try next time you boot going to the cli with Ctrl+Alt+F1, then login and issue the commands ```
sudo /etc/init.d/gdm stop
sudo apt-get update
sudo apt-get upgrade
```When that has finished, restart gdm with ```
sudo /etc/init.d/gdm start
```and then if needed ```
startx
```

---

### Post by mustangzach on 2009-08-21
actually, that fixed my HP. There's something weird about 9.04 when it's first installed; it's almost Windows like. The X server crashed multiple times until I updated it. Since then she's running fine. I'd like to mention it didn't do that on my Acer.

---

### Post by stlsaint on 2009-08-22
these acer systems are having a full list off issues with jaunty...i myself have had to roll back another system to an older version...if all else fails i recommend ubuntu christian edition...even tho you may not be a christian it is still a great OS for these acer laptops...and you can customize it to your liking...be it compiz, vbox, or amoarok...anything that works in jaunty or 8.10 or any other version works in christan edition and there is a forum on here in 3rd party projects where the developer of christian edition will full help you! trust me!!! and like i said its ubuntu just more compatible with these acer systems!!

---

### Post by ellis rowell on 2009-08-28
Thanks for that info., I'll give it a try.

---

### Post by cariboo on 2009-08-28
Moved to General Help.

---

