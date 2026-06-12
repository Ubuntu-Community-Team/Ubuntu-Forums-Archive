---
title: "Internet connects with pppoeconf but not able to browse"
date: 2010-10-09
forum: General Help
---

### Post by Chethan S on 2010-10-09
Just yesterday I posted a thread about not being able to browse some sites - [http://ubuntuforums.org/showthread.php?p=9942903#post9942903](http://ubuntuforums.org/showthread.php?p=9942903#post9942903)

The problem I believe is due to the MTU value and therefore I configured my connection using pppoeconf command. I used all default options there like connecting at startup as well. Now my problem is internet is connected at startup - it is evident from firestarter detecting hits, and the link light in my router glowing few times which is the usual way.

However any site for that matter loads only in the progress bar at 50% and after few minutes firefox cannot display the page. The "Activity" in firestarter shows upto 5 kbps and later comes down to 0.

I even tried editing various files like interfaces, dsl-provider as suggested in this link - [https://wiki.ubuntu.com/ADSLPPPoE](https://wiki.ubuntu.com/ADSLPPPoE)

---

### Post by dineshs on 2010-10-10
Since 10.04 uses Network manager,pppoeconf method may create problems.You may first backup  /etc/network/interfaces using
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```
Now run
```
 gksudo gedit /etc/network/interfaces
```
Let the file contain only these lines ```
auto lo
iface lo inet loopback
```
restart and connect using pon command.If you still have problems please let us know What you get for the following terminal commands```
ping 4.2.2.1 -c3
```and```
sudo gedit /etc/resolv.conf
```
by the way Why dont you configure your modem/router in PPPoE mode?What is the model name of your modem?

---

### Post by Chethan S on 2010-10-11
For me it was network manager which was causing a whole lot of problems. I couldn't browse many sites like [http://linuxtoday.com](http://linuxtoday.com), [http://earthexplorer.usgs.gov](http://earthexplorer.usgs.gov). The problems continued despite of changing the MTU value as suggested in many forums. Therefore I switched to pppoeconf. Now I have no problems with any website. 

For your information I use BSNL Broadband. Now the only issue I am facing is my internet does not connect at startup though I have configured it to do so at boot during the configuration phase as well as by editing the /etc/network/interfaces.

---

