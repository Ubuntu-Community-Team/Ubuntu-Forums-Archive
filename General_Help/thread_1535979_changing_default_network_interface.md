---
title: "changing default network interface"
date: 2010-07-21
forum: General Help
---

### Post by krnlcrash on 2010-07-21
I'm not sure if this is the right place for this question so forgive me, but having trouble setting up my ubuntu client to connect to openvpn server.

Actually the connection seems to work fine.  I followed these instructions: [http://www.hendlsofen.de/WRT54GL/eng/WRT54GL_OpenVpn.html](http://www.hendlsofen.de/WRT54GL/eng/WRT54GL_OpenVpn.html)

And connected.

My client created a new network interface called tap0 and I could ping the vpn server.

My problem is all web traffic still goes on the wlan0 interface.

My question here, what should I do to reroute traffic to use the vpn connection and not the wlan0 connection.  Specifically only need the web browser.

thanks

---

### Post by pytheas22 on 2010-07-21
I can't directly answer your question (my guess is that you need to change your routing tables, but I don't know how to do that off the top of my head), but you might want to try using the OpenVPN plugin for NetworkManager rather the command-line client that you installed following those instructions.  You can install the NetworkManager plugin by typing:
```

sudo apt-get install network-manager-openvpn-gnome
```

Then simply left-click on the NetworkManager applet, go to VPN Connections>Configure VPN and configure your VPN.  You should be able to use the same certificate files that you created previously.

---

### Post by prodigy_ on 2010-07-21
Probably you'll have to change your default route. The command to delete the old route: ```
sudo route del default
```
The command to add the new one is most probably: ```
sudo route add default dev tap0
```

Usually this does the trick, but depending on your network configuration you might need to add some other routes as well.

Please, keep in mind that you'll need to change your default route back to wlan0 if you'll deactivate your VPN.

---

### Post by prodigy_ on 2010-07-21
[edit: sorry, double post]

---

