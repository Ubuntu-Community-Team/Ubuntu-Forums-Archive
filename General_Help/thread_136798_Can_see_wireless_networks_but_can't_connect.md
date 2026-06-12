---
title: "Can see wireless networks but can't connect"
date: 2006-02-26
forum: General Help
---

### Post by Aikinai on 2006-02-26
Hi, I have a question about getting my wireless connection to work. I have a 3com 3CRSHPW196 PCMCIA wireless card (Xjack with antenna), and honestly I never expected it to work in Linux but Ubuntu recognized it (at least somewhat) right away. I know Ubuntu is talking to the card because I see network names and signal strengths (I'm using Network Manager Applet 0.4.1). It'll start connecting to the network, ask me for the WEP key, and then never finished connecting. I know this isn't a very technical diagnosis, but the light on the card doesn't blink when it's connecting like it does in Windows. It only blinks once or twice and then stops. Could this still be a driver issue, or is it something else since it's definitely talking to networks enough to get their names?
If it is a driver issue, it's probabl not worth messing with, but if it's just a simple problem with getting Ubuntu working wirelessly, I'd like to fix it. I'd appreciate any advice. Thanks a lot!

---

### Post by Ramses de Norre on 2006-02-26
I've had problems with the wep encryption, it didn't worked until I configured it manually in /etc/network/interfaces. 
Add a line ```
wireless-key wireless_key
``` there (with of course the key instead of wireless_key).
Static IP also works better as DHCP, you just need to type in all the numbers once;)

---

### Post by johninbanagher on 2006-03-04
I have the same card but i am having diferent problems. I am very new to Linux/Ubuntu and have found it a good alternative to XP but alas my wireless card on my laptop will not work for me.

Although my machine is seeing the wireless card and has accepted the wep key and all it still wont allow me to browse eithe the internet or my desktop

The little green light does not come on at all.

Please can anyone help me.

---

