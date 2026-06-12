---
title: "Desktop &amp; Server"
date: 2011-11-02
forum: General Help
---

### Post by Tribal-Wolf on 2011-11-02
I have an old pc I want to use as a server in the loft but it can only use a wireless network card as there is no way to get a cable up there. The problem I have is when I install Ubuntu server it cannot find the card, if I install desktop however the card is found instantly. How can I get server version to find and utilise the network card?

---

### Post by searchfgold6789 on 2011-11-02
Is [this]("https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint") what you are looking for?
Try making sure wireless tools are installed:
```
sudo apt-get install rfkill libiw30
```

---

