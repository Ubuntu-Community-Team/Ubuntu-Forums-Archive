---
title: "How do I find/create a hostname for VNC?"
date: 2010-12-17
forum: General Help
---

### Post by xlucidreamx on 2010-12-17
How do I make/find a host name in Ubuntu (10.04) so someone outside my local network can connect via VNC (Remote Desktop). I went to System> Preferences> Remote Desktop, but then it says 

"Your desktop is only reachable over the local network. Others can access your computer using the address 192.168.1.102 or geordie-desktop.local."

Any help will be much appreciated.
*Note, would this error be due to my ISP?

---

### Post by tredegar on 2010-12-17
192.168.1.102 is your LAN address.

If you go to [http://whatismyip.com](http://whatismyip.com) you'll get the INTERNET address of your router.

You now need to use your router's firewall configuration page to forward ports 5900-5909 to the LAN IP (192.168.1.102) of your PC.

Then they can connect to you at YOUR.IP.FROM.WHATISMYIP

Edit: Please be aware of the security implications of opening a port on your router's firewall.

Safer is to run vnc over ssh
There are many tutorials, here's [one]("http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html")
/Edit

---

### Post by xlucidreamx on 2010-12-17
Thanks, I appreciate your help!

---

