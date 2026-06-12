---
title: "PDANet working with Ubuntu"
date: 2009-10-18
forum: General Help
---

### Post by subsity on 2009-10-18
Ok before I upgraded to the new Ubuntu 9.10 this script worked with pdanet to tether my iphone. I was wondering if anyone out there can help me get it working again. Please this is my first post so be gentle. Thanks and I have used linux since 8.04 version and I love it!

I am going to post both scripts. Thanks to All the people who have contributed to the success of Ubuntu!
**This is the first script that allows me to get it working. **

> 
#!/bin/sh
# pdanet_on
sudo /etc/init.d/NetworkManager stop
sudo ifconfig eth1 down
sudo iwconfig eth1 mode ad-hoc
sudo iwconfig eth1 channel 4
sudo iwconfig eth1 essid 'laphone'
sudo iwconfig eth1 key cA1158tO
sudo ifconfig eth1 up
echo Press Enter when iPhone is connected to Network and PDANet is started
read foo
sudo dhclient eth1
DNS=`grep nameserver /etc/resolv.conf | head -1 | awk '{print $2}'`
dig @$DNS [www.google.com]("http://www.google.com")
[B]This is the second script to bring my network manager back and running
[/B] 
> 
#!/bin/sh
# pdanet_off
sudo ifconfig eth1 down
sudo iwconfig eth1 mode managed
sudo ifconfig eth1 up
sudo /etc/init.d/NetworkManager start


**[COLOR=Black]Here are the errors I get now when I run this script[/COLOR]**

> 
sudo: /etc/init.d/NetworkManager: command not found
eth1: ERROR while getting interface flags: No such device
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "cA1158tO".
eth1: ERROR while getting interface flags: No such device
Press Enter when iPhone is connected to Network and PDANet is started



---

### Post by EvilZero65 on 2009-11-04
I was also having problems with PDANet on Karmic. I tried your scripts, but was getting similar errors till I modified them as follows:

```

#!/bin/sh
# pdanet_on
sudo service network-manager stop
#sudo /etc/init.d/network-manager stop
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode ad-hoc
sudo iwconfig wlan0 channel 4
sudo iwconfig wlan0 essid 'IphoneAdHoc'
sudo ifconfig wlan0 up
echo Press Enter when iPhone is connected to Network and PDANet is started
read foo
sudo dhclient wlan0
DNS=`grep nameserver /etc/resolv.conf | head -1 | awk '{print $2}'`
dig @$DNS www.google.com
```

Then Network Manager back up:

```
#!/bin/sh
# pdanet_off
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed
sudo ifconfig wlan0 up
sudo service network-manager start
```


I changed my interface to wlan0, not sure if this would work on your system. I didn't try encryption but I am assuming it would work. Oddly, I was able to connect though network manager after I ran the second script. As a side note I am running PDANet version 1.61 which was just released in Cydia.

---

