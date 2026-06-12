---
title: "Vista will connect to wireless router but ubuntu will not"
date: 2009-10-12
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-10-12
I set up Vista w/ my wireless router and will connect fine. When I installed wubi and booted into Ubuntu, Ubuntu will not connect to the router. I am posting this from the ubuntu system (hardwired). What kind of setup do I need to perform to get Ubuntu to connect to the router wirelessly? Running Ubuntu Jaunty 9.04

---

### Post by PrePenguin on 2009-10-12
Disable Lan in Bios and reboot back to ubuntu and see if the wireless starts working and if that dont work please post the maker of your wireless card..

---

### Post by cwbar_1 on 2009-10-12
Go to System > Administration > Hardware Drivers and see if it lists a wireless card driver.  If it does, enable the driver, and disconnect the wired connection.  Then choose your wireless network.

---

### Post by Feelin_froggy8877 on 2009-10-12
The proprietary driver loded and activated is "broadcom sta wireless driver" The make of the router is Linksys by Cisco

---

### Post by cwbar_1 on 2009-10-12
Are you saying that it works now?

---

### Post by PrePenguin on 2009-10-12
> **Feelin_froggy8877 said:**
> The proprietary driver loded and activated is "broadcom sta wireless driver" The make of the router is Linksys by Cisco
  
 
Did this fix this? Broadcom someone else just loaded the proper driver as mentioned above and started working for this make.. If not please report on what you have did so far on the suggestions..

---

### Post by Feelin_froggy8877 on 2009-10-12
Sorry, no I'm not, the driver has been loaded since first boot up after install.

---

### Post by Feelin_froggy8877 on 2009-10-12
I will go into bios now and report back (asap)

---

### Post by cwbar_1 on 2009-10-12
Some simple suggestions first....Right click on the network applet and make sure "Enable Wireless" is ticked.  Then left click the network applet and see if your connection is visable.  If you have your wireless set up as "Hidden," there is a choice for this as well.  If these don't do it, copy and paste the output of "ifconfig" and "iwconfig."

---

### Post by Feelin_froggy8877 on 2009-10-12
Cancel that, Gonna let upgrades finish. Don't think it will take care of my problem due to proprietary drivers.

---

### Post by jim_joh on 2009-10-12
have a Asus eee pc 1000he with 60gig ssd so yesterday I wiped xp off and installed Ubuntu 9.10. Everything worked fine except the wireless would not reconize my router. I tried eveything with no luck. I wired my eee to the router went to the EEE pc 1000he download page and downloaded the latest xp driver. Well Asus hid the driver in a in a install package. I then installed the window wireless driver package, finally was able to steer it to the driver, installed and bingo the wireless now work great. All I can say is do I now have a very fast netbook & very happy. Just wanted to share. jim_joh

---

### Post by PrePenguin on 2009-10-12
When u say proprietary I am assuming you are refering to these drivers here? [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) and incase your wondering this is the hidden package everyone is refering to ......ubuntu-restricted-extras  it sometimes cures the issue and sometimes dont i have seen it work both ways on wireless..

---

### Post by Feelin_froggy8877 on 2009-10-12
ok, left clicking network applet shows my "lynksys_xxxxx" when i try to tick it it is asking for a password for encryption????

---

### Post by PrePenguin on 2009-10-12
Yes you will have to enter your WEP key if thats what it uses on windows too to protect your network. And can you mention what has made the card start working?

---

### Post by Feelin_froggy8877 on 2009-10-12
O.k no extra configuration required, had to call verizon and find out my passphrase, thats it...thank you for the replies. Connected through the wireless router now. ;-)

---

### Post by Feelin_froggy8877 on 2009-10-12
Is my password the for for shared folerd (connection tonetwork)?

(edit) sry, password for my network is login pass.


Hope all the posts are ok, Will be soon, I will be answering posts ;-)

---

### Post by PrePenguin on 2009-10-12
> **Feelin_froggy8877 said:**
> Is my password the for for shared folerd (connection tonetwork)?
 
 
It is the administrative password required to access root.  if thats what you are refering too not sure if I understand what you are asking here.

---

### Post by Feelin_froggy8877 on 2009-10-12
Thats it exactly. thank you.

---

