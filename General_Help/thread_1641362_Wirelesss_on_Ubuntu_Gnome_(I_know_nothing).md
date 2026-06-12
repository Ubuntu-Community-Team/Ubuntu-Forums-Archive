---
title: "Wirelesss on Ubuntu Gnome (I know nothing)"
date: 2010-12-08
forum: General Help
---

### Post by canboy975 on 2010-12-08
I have had ubuntu for several months now and my wireless has worked just fine, but all of a sudden it just turned off. In the drop down menu in the top right corner for wirless it has a check mark beside "enable networking" but the button "enable wireless" is greyed out and I cant click it. I have checked that the wireless is working and it is (confirmed with another laptop). Any help would be greatly appreciated. thanks

---

### Post by thameera on 2010-12-09
The "Enable Wireless" switch usually greys out when the network enabling switch of the computer is turned off. Make sure it's turned on. If it's already turned on, try turning it off and connecting. This may work if the switch positions have been confused by the machine.
If this didn't work, try the command
```
nmcli nm wifi on
```
in the terminal. This is the command used to turn on wireless.

---

### Post by canboy975 on 2010-12-09
thank you! i didn't realize there was a physical switch on my laptop to turn wireless on and off. And it was in the on position and once i flipped it, boom! wireless

---

