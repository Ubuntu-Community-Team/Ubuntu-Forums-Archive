---
title: "HOW:TO  get a huwei HDSPA working in Karmic"
date: 2009-10-30
forum: General Help
---

### Post by dj-toonz on 2009-10-30
Open up places, Computer & if you see a virtual CD ROM & a SSD card Reader

right mouse click on the Virtual CD ROM (you don't need it as there windows drivers) & select safety remove device)

then when the SSD card reader & virtual CD ROM has Gone , close the computer browser box


open a terminal up

Applications , Accessory , Terminal

then copy & paste these following commands (there just to get your modem to be seen by network-manager)

sudo rmmod usb-storage

[enter your user password if asked for it] then can follow on with the rest without entering your user password

sudo modprobe -r option

sudo modprobe -r usbserial

sudo modprobe usbserial vendor=0x12d1 product=0x1001

or

sudo modprobe usbserial vendor=0x12d1 product=0x1003 [If the first code doesn't work]


Then lastly

sudo pppd ttyUSB0

& don't forget to close the terminal box when finished with it


then when you goto Network-Manager & right mouse click on edit connections, Mobile broadband, Add a connection , your modem will now be showing like it is in the screen shot

[[ UPDATE ]] Just been told, if it doesn't work first time around, insert a MicroSD card in the modem before inserting into the machine ??? funny that,, but somebody said it worked for them that way, thought I would mention it, other wise I would be getting told off

And the screen shots to show the modem not working before I used the following commands & the modem working after.


P.S you have to do the following the first time you want to connect using the connection. After that you can disconnect & connect all you want, just make sure you don't reboot other wise you will have to repeat the above to get the connection working again

"" Also don't remove the modem & plug it back in or you you will have to do the above commands again for network-manager to see the modem ""

now you can surf to your hearts content :popcorn:


Big shout out & credit goes to dmwelsch for letting me know about the MicroSD card tip & unpluging the modem & pluging it back in , that you have to re-do the above commands for network-manager to see the modem or reboot the system to get it working again

---

