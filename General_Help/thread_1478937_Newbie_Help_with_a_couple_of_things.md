---
title: "Newbie Help with a couple of things"
date: 2010-05-10
forum: General Help
---

### Post by IAmTheDude360 on 2010-05-10
Hey guys, finally had the time to sit down and spend time with Linux, been a long time coming and loving it so far :)

Dual booting 10.4 with Win7 on my laptop I use for college and so far Ive been able to figure out and learn everything Ive needed but having a little trouble with a couple of things.

1)
I need to change my MAC at boot, Ive been able to figure out how to do it manually from terminal once booted and it seems to work fine, Im just a little lost when it comes to the startup script.

The reason for the mac change is my old laptops mac is registered with college but this new one isnt. Ive bugged the IT dept for several months now to have it updated to my new one but with no response and as its coming up to the end of term I cant see it being done before then. Ive changed it easily within Win7 to my old one but am struggling doing it automatically with Linux.

This is what Ive been able to get so far:

Terminal:

ifconfig wlan0 down
ifconfig wlan0 hw ether xx:xx...
ifconfig wlan0 up 

Ive tried putting the info into /etc/network/interfaces but all the posts Ive seen to do this seem to have different contents, all mine contains is

auto lo
iface lo inet loopback

and the spoofing doesnt work when its placed in there.

Then I found a startup script that everyone says works fine,

ifconfig

cd /etc/init.d

sudo nano ChangeMAC

Then, fill configuration file with new MAC Address.
sudo ifconfig eth1 down
sudo ifconfig eth1 hw ether xx:xx:xx:xx:xx:xx
sudo ifconfig eth1 up
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking restart

Save and close the file

Apply configuration file.
$ sudo chmod +x ChangeMAC

$ sudo update-rc.d ChangeMAC defaults 

Now, when I update-rc.d I get an error concerning the lsb info.
After a bit of research I understood that the ChangeMAC file needs a header, this is what it looks like so far:

### BEGIN INIT INFO
# Provides:          changemac
# Required-Start:
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: changemacatboot
# Description:       Change MAC at boot.
### END INIT INFO

sudo ifconfig wlan0 down
sudo ifconfig wlan0 hw ether 12:13:02:4e:32:e0
sudo ifconfig wlan0 up
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking restart,

after update-rc.d I get no errors but the script doesnt seem to run at boot.

This is where I get lost, could someone point me in the right direction?

2)
Drivers. Little bit lost as to how this all works compared to Windows.

Everything on the lappy works fine, webcam, card reader etc and Im assuming the graphics are working ok as I have a decent looking display and am able to use the majority of effects with compiz rain, wobbly windows etc but not the advanced ones like window blur.

I have a ATI Mobility Radeon X1400 512mb but nothing appears in hardware drivers. Are the best drivers automatically installed? The catalyst control centre cannot find any drivers for it or am I missing anything?

Finally,

I use a backup program called Macrium Reflect on Windows to create regular disk images using VSS. This gives a quality snapshot without a massive filesize.

Now I can backup the entire ext4 partition from within 7 but that gives a massive 1:1 image and I havnt got round to trying the restore of it yet in case it doesnt work.

What would be the best Linux equivalent?


Appreciate any help or pointers you could give. Doing ok so far and loving it :D

TIA

---

### Post by Kljuka on 2010-05-10
You should know, that you are usinig SysV INIT, which is the old way of startup scripts.
The new way is with Upstart (but if I'm correct, it implements parts of the old system):
[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

Try Putting at the beginning (first line) something like:
#!/bin/bash

This tells Ubuntu with what program to run the script (/bin/bash).
Then try it in the terminal to check if it works. Run that way:
```
./ChangeMAC
```

---

### Post by IAmTheDude360 on 2010-05-11
Thats brilliant :)

Works at startup no problems now. Unfortunately Im now running into problems using the new spoofed mac :( Seems even though the mac has successfully changed it will no longer connect.

Tried on my home network last night with the same results. Looking around the net it seems its a common problem as well so I dont think Ill be able to fix this one. Stuck using Win7 at college for now then :(

Could still use some guidance on my other issues, appreciate it :D

---

