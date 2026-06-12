---
title: "Internet Problem"
date: 2006-02-02
forum: General Help
---

### Post by malic on 2006-02-02
Hi!
I've installed ubuntu 5.10 yet, but i can not open web pages by firefox. My connection type is cable DSL and IP Number is dynamic. When i plug out the eternet cable, my computer reacts and link led of DSL Modem turns off. I looked at the network settings. Everything was OK.( Eternet connection is active, DHPC mode is enabled). I did ping test also and saw the transferred packets. I could not understand what the problem is.

---

### Post by oicu on 2006-02-02
what is written in the resolv.conf file?

---

### Post by malic on 2006-02-02
Thank you for your reply, but i am freshman linux user. How can i see the resolv.conf file. If you say location of the file, i can find.

---

### Post by johnnymo87 on 2006-02-02
I believe you type this: 
```

gedit /etc/resolv.conf

```

I just used the search option with my ubuntu desktop to find the file. Does anyone know a way to search my computer for a file from the terminal?

---

### Post by dcstar on 2006-02-02
[QUOTE=johnnymo87]I believe you type this: 
```

gedit /etc/resolv.conf

```

I just used the search option with my ubuntu desktop to find the file. Does anyone know a way to search my computer for a file from the terminal?[/QUOTE]
"find" (use "man find" for the many, many options on how to use this powerful command - but it can be tricky to use for a novice user).

---

### Post by malic on 2006-02-03
[QUOTE=malic]Hi!
I've installed ubuntu 5.10 yet, but i can not open web pages by firefox. My connection type is cable DSL and IP Number is dynamic. When i plug out the eternet cable, my computer reacts and link led of DSL Modem turns off. I looked at the network settings. Everything was OK.( Eternet connection is active, DHPC mode is enabled). I did ping test also and saw the transferred packets. I could not understand what the problem is.[/QUOTE]
[B]
I opened "resolv.conf" file, it is written that "nameserver 192.168.1.1". This is the number that opens DSL modem interface software when i write this in adress bar of any web browser. I still have internet problem with ubuntu.[/B]

---

### Post by steve.horsley on 2006-02-03
[QUOTE=johnnymo87]I believe you type this: 
```

gedit /etc/resolv.conf

```

I just used the search option with my ubuntu desktop to find the file. Does anyone know a way to search my computer for a file from the terminal?[/QUOTE]
Quickest is the locate command.
locate filename

---

### Post by gravediggers on 2006-02-03
You could try the following!

in the location bar in firefox type about:config
then in the filter type network
scroll down till you find network.dns.disableIPv6
right click, choose toggle, and it changes to true
this hopefully will cure it!:)

---

### Post by malic on 2006-02-03
[QUOTE=gravediggers]You could try the following!

in the location bar in firefox type about:config
then in the filter type network
scroll down till you find network.dns.disableIPv6
right click, choose toggle, and it changes to true
this hopefully will cure it!:)[/QUOTE]
[B]
Thank you for helping me. I applied your instructions, and now i am on ubuntu and writing message to ubuntu forum on account of you. Again thanks alot. My internet problem was solved by guidance of your intructions. :) \\:D/ [/B]

---

