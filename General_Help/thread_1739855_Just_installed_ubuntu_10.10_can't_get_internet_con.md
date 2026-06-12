---
title: "Just installed ubuntu 10.10 can't get internet connection?"
date: 2011-04-26
forum: General Help
---

### Post by wayofthedragon on 2011-04-26
I just installed ubuntu 10.10 and it isn't detecting my wireless connection. Someone told me I need drivers installed i am dual booting and was just wanting to install them from windows though. Could someone give me a link to where i would download the drivers? Also someone told me i need to have a card? What is card?

---

### Post by KegHead on 2011-04-26
Hi!

You can install drivers in [COLOR="Red"]Ubuntu[/COLOR] via:

system...preferences...additional drivers

install

Keghead

---

### Post by TeoBigusGeekus on 2011-04-26
Go to Administration>System>Hardware Drivers
Are there any proprietary drivers for your wireless card there?
If so, enable them.

---

### Post by Quackers on 2011-04-26
Welcome to UF.
If you have an ethernet cable you can connect it and install the wireless/graphics drivers through that connection. Via System > Admin > Additional Drivers.
The card would presumably be a wireless card?

---

### Post by KegHead on 2011-04-26
Hi!

Sorry!

"admin' is correct...I'm on the metro!

KegHead

---

### Post by wayofthedragon on 2011-04-26
> **TeoBigusGeekus said:**
> Go to Administration>System>Hardware Drivers
Are there any proprietary drivers for your wireless card there?
If so, enable them.

I don't have a wireless card, it gave me a wired card. I was just wanting to install the drivers through windows though and save them to a place i can access them through ubuntu.

---

### Post by wayofthedragon on 2011-04-26
> **Quackers said:**
> Welcome to UF.
If you have an ethernet cable you can connect it and install the wireless/graphics drivers through that connection. Via System > Admin > Additional Drivers.
The card would presumably be a wireless card?

I've already went to that it didn't detect any drivers

---

### Post by Quackers on 2011-04-26
Was that with an ethernet cable plugged in?

---

### Post by TeoBigusGeekus on 2011-04-26
Can you also open a terminal (applications>accessories>terminal) and post us the output of
```
lshw -C network
```
?

---

### Post by wayofthedragon on 2011-04-26
> **Quackers said:**
> Was that with an ethernet cable plugged in?

No. I was just thinking that when i installed it that it would automatically detect my wireless connection that i have but it won't. I don't know I know absolutely nothing about computers at all lol i just made this account up to get on here and ask this question.

---

### Post by wayofthedragon on 2011-04-26
> **TeoBigusGeekus said:**
> Can you also open a terminal (applications>accessories>terminal) and post us the output of
```
lshw -C network
```
?

K hold on.

---

### Post by Quackers on 2011-04-26
> **wayofthedragon said:**
> No. I was just thinking that when i installed it that it would automatically detect my wireless connection that i have but it won't. I don't know I know absolutely nothing about computers at all lol i just made this account up to get on here and ask this question.

I would try to find an ethernet cable and run the Additional Dirvers utility again.

---

### Post by JaYC1193 on 2011-04-26
hey.... im having the same problem i have plugged my ethernet cable into my laptop and my laptop has built in wireless and when i try connecting to any wireless modem it fails to establish :s and i also did system>administration>additional drivers.... and it said no drivers were found.... (ethernet cable plugged in all the time) i duno what else i can do :S

---

### Post by wayofthedragon on 2011-04-26
> **Quackers said:**
> I would try to find an ethernet cable and run the Additional Dirvers utility again.

Ya just gonna do that i guess. Thanks guys.

---

### Post by KegHead on 2011-04-26
Hi!

Click on the icon..(upper right hand side) and select you wifi connection.

KegHead

---

