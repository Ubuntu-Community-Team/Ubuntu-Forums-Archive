---
title: "VPN connection to work"
date: 2006-04-30
forum: General Help
---

### Post by Goonie on 2006-04-30
Hi

I work a bit from home and I connect to work using a VPN connection I set up in Windows. Now I am really trying not to use Windows at home but I don't know how to connect to the lan at work via Ubuntu. Now I boot up in Windows -> connect to work -> copy the files I need-> reboot into Ubuntu -> mount my Windows partition and access the files from there.  This is very tiresome.

Can I connect to my network at work via Ubuntu? I there an option/tool that lets me setup a VPN tunnel as easily as Windows does? Thx.

Goonie

---

### Post by Koybe on 2006-04-30
You'll find a howto to connect to a PPTP VPN server here : [http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)

It's fairly easy to set up. The only real prob comes with routing. But the graphical client is helping a lot.

GL ;-)

---

### Post by drfox on 2006-04-30
You have to be root in order to use pptpconfig.

Larry

---

### Post by Koybe on 2006-04-30
Just make a script using gksudo... it works fine ;)

---

