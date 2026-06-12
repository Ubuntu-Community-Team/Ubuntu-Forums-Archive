---
title: "network manager issues"
date: 2010-11-08
forum: General Help
---

### Post by bazerka on 2010-11-08
Ok so i have checked, network manager is installed, just the problem is i cant see it in the notification area... ppl keep telling me to add it on the panel and it will show, well its not... all i see are 3 small dashes stacked on each other. The network manager is running, so any1 got any ideas?

---

### Post by wojox on 2010-11-08
Wired or wireless?

Which Ubuntu version?

---

### Post by bazerka on 2010-11-08
srry im using a wired connection, but i want my wireless connection, and version 10.10 normal ubuntu 64 bit

---

### Post by vrhahaha on 2010-11-08
Have u tried restarting your gnome-panel?

try Alt+F2 then type killall gnome-panel

i do that whenever something's wrong with my applet

---

### Post by wojox on 2010-11-08
So you can use it, just not see it?

---

### Post by wojox on 2010-11-08
> **bazerka said:**
> srry im using a wired connection, but i want my wireless connection, and version 10.10 normal ubuntu 64 bit

You probably need to install the driver. Is there anything in Hardware Drivers?

What card do you have?

```
lspci | grep -i net
```

---

### Post by bazerka on 2010-11-09
ok the gnome restart didnt work, and here is my card version

08:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
 but i dont think thats it, cause my wireless can work fine, (the switch says its turned on) and i installed the driver and what not, its just i cant SEE the network manager icon in my gnome panel thats all

---

### Post by dr_duck on 2010-11-09
Hi,

I have a similar problem but in my case the nm icon doesn't show for the second user who logs in (via switch user).  It only shows for the first user who logs in.

My thread is over here: [http://ubuntuforums.org/showthread.php?t=1616445](http://ubuntuforums.org/showthread.php?t=1616445)

---

### Post by wojox on 2010-11-09
> **bazerka said:**
> ok the gnome restart didnt work, and here is my card version

08:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
 but i dont think thats it, cause my wireless can work fine, (the switch says its turned on) and i installed the driver and what not, its just i cant SEE the network manager icon in my gnome panel thats all

Try changing themes and see what happens.

---

### Post by bazerka on 2010-11-09
Lol nope, but i think i got it cause i have a pppoe connection apparently it removes the network manager icon, ugh i dont like pppoe bleh

---

### Post by dineshs on 2010-11-11
Please try STEP-I  [here]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2")  then  restart.If your icon is back and you want DSL connection via ethernet,try STEP-III

---

### Post by bazerka on 2010-11-15
Okies ill try that, but i have to reinstall Ubuntu again, so ill wait till the weekend. thanks tho! :D

---

### Post by bazerka on 2010-11-16
Psh couldn't wait till the weekend, but IT WORKS! woot! and i think it solved the disconnection error as well so thank youu!!!!

---

