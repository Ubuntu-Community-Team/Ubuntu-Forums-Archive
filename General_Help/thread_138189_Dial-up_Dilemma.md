---
title: "Dial-up Dilemma"
date: 2006-03-01
forum: General Help
---

### Post by doc_kamolly on 2006-03-01
I just got UBUNTU yesterday, and although I haven't utilized it to the fullest, I can see it has potential.

Anyway, I want help in getting the GNOME dial-up tool so I can get internet on the OS. Can anybody tell me where or how can I get it?? Please guys and gals, I need your assisstance.

Thank you.

---

### Post by Bachstelze on 2006-03-01
You propably have a "winmodem", this is always a problem on linux... See [http://www.linmodems.org](http://www.linmodems.org) for further info.

---

### Post by amosbatto on 2006-03-01
Goto: Applications -> Internet -> GNOME PPP

I think the gnome dialup tool comes with ubuntu, but if you can't find it:
sudo apt-get install gnome-ppp

Refresh the Gnome panel:
killall gnome-panel


If you want to use the command line:
To configure dialup: 
sudo pppconfig

To connect dialup: 
sudo pon provider_name

To disconnect dialup: 
sudo poff


I find that KDE's dialup tool kppp is much better, so you might want to download that.

---

### Post by StefanoCole on 2006-03-02
doc_kamolly welcome to Ubuntu, have you already checked this wiki?: [https://wiki.ubuntu.com/DialupModemHowto?highlight=%28modem%29]("https://wiki.ubuntu.com/DialupModemHowto?highlight=%28modem%29")

Stefano

---

### Post by akiro.yamamoto on 2006-03-02
On a fresh install of Breezy (5.10) you will not have Gnome-ppp available.
As long as you have the drivers for your WinModem or you have a modem 
supported by Linux you have two options.
1) Go online (M$ Win) and download Gnome-ppp .deb package (Google), then install 
it in Ubuntu.
2) Use the networking tool to set-up your internet account.
Go to System>>Administration>>Networking.
It is fairly self explanatory. when your done I would recommend getting gnome-ppp
anyway as the Networking tool is a little like overkill to get online. I think it's a bit 
clunky. Gnome-ppp is a lot more stream lined and easier to understand.

---

