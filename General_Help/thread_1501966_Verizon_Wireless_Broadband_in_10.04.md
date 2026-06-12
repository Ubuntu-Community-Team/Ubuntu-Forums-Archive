---
title: "Verizon Wireless Broadband in 10.04"
date: 2010-06-04
forum: General Help
---

### Post by mac9416 on 2010-06-04
Hello, all!

I have just installed lubuntu 10.04 on my old IBM laptop. I'm almost completely happy with everything except that Network Manager isn't recognizing my Verizon mobile broadband card. 

I'm not sure what it all means, but on the card is printed "QUALCOMM 3G CDMA" and "PC5750."

[Someone on the Keryx forums]("http://keryxproject.org/forums/index.php?page=findpost&post=306") mentioned that they had the same problem, and that they solved it by installing the latest version of usb-modeswitch and usb-modeswitch-data from the Debian repos. I've done this with no improvement. 

I'm a bit frustrated. Thanks for any help!

---

### Post by v1ad on 2010-06-05
[http://www.backtrack-linux.org/tutorials/3g-modems/](http://www.backtrack-linux.org/tutorials/3g-modems/)

here is a link, that is done in backtrack. it runs a older version of ubuntu kernel.

---

### Post by mac9416 on 2010-06-06
Hi, v1ad,

Thanks for the link. I am tickled pink to now be posting from what was an offline computer. I followed the tutorial to the letter, only changing "ttyUSB0" to "ttyACM0" in /etc/ppp/peers/vzw.

Now I have another problem:

The connection drops every now and then (the last one lasted 17.3min.), so I have to go back and run the commands to reconnect. This can be made easier by creating a script and dropping a launcher of it into the panel for convenience. However, I would much prefer a solution that allows me to connect using Network Manager.

Still, this is a big step forward. Thanks for the help!

---

### Post by efflandt on 2010-06-06
If pcmcia recognizes your card, not sure why it would not work automatically with Network Manager.  I have an older USB720 (Novatel) card, and all I had to do in Network Manager was select my country and Verizon, and it simply worked.  Of course you should check the boxes to "Connect automatically" and "Available to all users".

---

### Post by mac9416 on 2010-06-06
Hi, efflandt,

Well, here's what happens when I try to use Network Manager to connect.

1) Right-click the Network Manager applet and choose "Edit Connections."
2) Go to the Mobile Broadband tab.
3) Click the Add button.
4) On the first page the device dropdown is grayed out. This is the first hint that my device is not recognized.
5) Go to the next page, leave the default of USA, and continue.
6) Choose Verizon as my provider.
7) Review the information and click Apply.
8) The connection editor comes up automatically, and I choose Connect Automatically and Make available to all users.
9) Click Apply and provide my password.

In 9.10, that would have done the trick. But in 10.0, my new connection doesn't appear in the Network Manager applet, just as if the device isn't recognized. I've unplugged and replugged the card and rebooted multiple times. Still no luck.

---

### Post by mac9416 on 2010-06-12
I managed to get the connection set up with GnomePPP and wvdial. The instructions are a bit extensive, so I'll link to my blog post about it: [http://mac9416.com/2010/06/12/connecting-to-verizon-mobile-broadband-in-ubuntu-10-04/](http://mac9416.com/2010/06/12/connecting-to-verizon-mobile-broadband-in-ubuntu-10-04/)

---

