---
title: "modem"
date: 2006-02-17
forum: General Help
---

### Post by andy5667 on 2006-02-17
Hey i have drivers for my bt voyager 105 modem but i am unsure how to install them. Its the top download on this site. [http://eciadsl.flashtux.org/download.php?lang=en]("http://eciadsl.flashtux.org/download.php?lang=en")
Please help asap so i can start using ubuntu.

---

### Post by sarah_b on 2006-02-17
Welcome to the forums andy5667,

Is your modem a external or internal ? I have not seen many people get a internal to work without some "majic", on the other hand externals do work in Linux/ubuntu. Externals do not really cost that much, usually on Ebay for $15-$20 but they are worth it to avoid headaches.

Here is a link you can check out:
[try this]("https://wiki.ubuntu.com/DialupModemHowto")

My favorite way to set up a modem was using "pppconfig". You can do that by opening a terminal and enter the following command and then just follow the directions:

[COLOR="DarkOrange"]**sudo pppconfig**[/COLOR]

good luck on getting your modem to work,
sarah

---

### Post by sarah_b on 2006-02-17
I forgot to add, once you have set up a external modem through "pppconfig", to get your modem connected, from a terminal enter:
[COLOR="DarkOrange"]**Sudo pon my_ISP**[/COLOR] (my_ISP is what you named your connection in "pppconfig") 

Then to close down the connection from a terminal enter:
[COLOR="DarkOrange"]**Sudo poff my_ISP**[/COLOR]

---

