---
title: "Wicd + iwconfig is hosed, please help!!"
date: 2009-09-04
forum: General Help
---

### Post by azredwing on 2009-09-04
In attempting to solve a problem in this thread [http://ubuntuforums.org/showthread.php?p=7895140#post7895140](http://ubuntuforums.org/showthread.php?p=7895140#post7895140) , on my Thinkpad T61, I somehow hosed my wireless connection.

Long story short, I ran

> 
$ sudo iwconfig wlan0 essid off


to see if I my computer would shut down properly. (It does.)

So I booted up and ran
> 
$ sudo iwconfig wlan0 essid on
 

and nothing happened. Restarted.

When I booted up again, Wicd couldn't connect to my wireless network - it error'd out, saying that it couldn't get an ip.

Running 

> 
$ iwconfig wlan0


shows that I can see my wireless network just fine, and running

> 
$ iwlist wlan0 scan


did at some point show all the available wireless networks - but now it's saying "resource unavailable" or unable to find any networks.

Sometimes after the lappy is restarted, Wicd can scan and successfully see the surrounding wireless networks - but then it can't connect to mine, and then it says that there aren't any wireless networks around.

Any ideas what is going on??

---

