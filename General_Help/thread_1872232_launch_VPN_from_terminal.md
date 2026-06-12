---
title: "launch VPN from terminal"
date: 2011-10-30
forum: General Help
---

### Post by g999b on 2011-10-30
Hi, I'm using 11.10, it works fine.

I have set-up a VPN access which I turn on from the network menu on top of the screen. Everything works ok. I was just wondering if there is a way to launch the VPN directly from the Terminal and not for the menu?

Thanks for your help
g999b

---

### Post by infinitybot on 2011-10-30
Assuming that you use OpenVPN ( **sudo apt-get install openvpn network-manager-openvpn -y** );
Run the Command :  "sudo openvpn --config <your-path-to-to-conf-file> "
For Example if your conf file is located @ /home/foo/personal.conf  , It will be "sudo openvpn --config /home/foo/personal.conf"

Hope this helps you 
:popcorn:

---

### Post by g999b on 2011-11-04
Thanks infinity. Appreciate your help. I'm not using Open VPN (yet), I'm using the built in VPN app in the network menu on 11.10.
I'm gonna try to configure openvpn, hope it's easier than send mail :D #geekjoke

Have a great day ahead!

---

