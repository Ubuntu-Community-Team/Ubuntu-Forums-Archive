---
title: "wifi dongle woe's"
date: 2012-01-15
forum: General Help
---

### Post by Smilax on 2012-01-15
hi, 

i'm tring to connect to my wifi network from a usb wifi dongle 

the reason is my internal card can't resolve the signal due to being at the other side of the house.

the wifi dongle shows full bars on the wifi panel dropdown menu but won't connect

it's a micronext MN-WD150B
Realtek 802.11n WLAN Adapter

when i bring my computer to the wifi router my internal card connects no trouble at all.

when i click connect on the wifi dongle part of the menu it shows those 2 green lights and the blue shape circlin for ~30s then it askes me for the password 

here's where it gets weird. 
it shows the box,

Authentication required by wireless network,

but shows my internal card a s first option, 

i change it to usb dongle but get nowhere agian

when i select the usb dongle again it repaets the greenlights bit. 


anyone any clue what i should try

regards,

Smilax

---

### Post by Smilax on 2012-01-16
ok, just for any future wifi woe's for other's i've found the solution.

thx to [atconley]("http://ubuntuforums.org/member.php?u=1470521")

from page 12 in this thread,..

[http://ubuntuforums.org/showthread.php?t=1861463&page=12](http://ubuntuforums.org/showthread.php?t=1861463&page=12)

> **atconley said:**
> Hello all.  **Andrew** here from **post #3**.  I've now managed to solve my particular problem (with thanks to *Xavi López* and *heartsmagic* at [askubuntu.com]("http://ubuntuforums.org/askubuntu.com") for the post that caused me to understand what was happening; see [here]("http://askubuntu.com/questions/77314")).   Judging by the many posts on this thread, others have a variety of  issues that appear to me to be different from my own.  Nonetheless, I  will post what I did in case it is of use to someone else.  I hope it  is.

**DESCRIPTION OF PROBLEM:**
- Ubuntu 11.10
- USB wireless 'mini'-dongle
- connects to network but no internet
- LED always on
[B]
SOLUTION:[/B]
- download most recent driver from [here]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true#2772") then unzip/extract the ZIP file
- change the permissions of *install.sh* to allow execution of it as a program
```
chmod 775 install.sh
```- install the driver (when asked, select '1' for '8192cu')
```
sudo ./install.sh
```- open */etc/modprobe.d/blacklist.conf*
```
sudo gedit /etc/modprobe.d/blacklist.conf
```- blacklist the  old module (which is included in the kernel) by adding the following  line to that file:
```
blacklist rtl8192cu
```- open [I]/etc/modules
[/I]```
sudo gedit /etc/modules
```- add the new driver to the list  of custom/additional modules that are loaded at boot by adding the  following line to that file:
```
8192cu
```- restart your computer to prove that it works
- sit back and enjoy your internets :cool:


:guitar::guitar::guitar:

---

