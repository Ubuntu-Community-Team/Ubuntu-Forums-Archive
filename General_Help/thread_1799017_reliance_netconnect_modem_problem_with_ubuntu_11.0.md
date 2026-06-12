---
title: "reliance netconnect modem problem with ubuntu 11.04"
date: 2011-07-07
forum: General Help
---

### Post by adithyajones on 2011-07-07
I have ubuntu 11.04 in my netbook and when I inserted reliance netconnect broadband usb modem,it automatically detected and after giving the necessary details  it was connected..But I am not able to access any websites..On googling I found that I have to make changes to /etc/resolv.conf..But resolv.conf file is missing..Kindly advice..

---

### Post by kanishkdudeja on 2011-07-07
well..did u install the setup given in the cd?

That crossplatform stuff..

i use reliance netconnect too..

that installer doesnt work for me..

all i did was go to network connections..

under mobile broadband create a new connection..

then select reliance from the subscriber list..

then when they tell you to enter username password..enter it..

and  number is #777

unplug ur reliance netconnect..plus it again..after 2-3 mins..it automatically gets connected and you will be able to use it.

---

### Post by createdcreature on 2011-07-07
Nearly all dial-up/mobile broadband modems do not work properly with any type of Linux. I use Wi-Fi and Ethernet.

---

### Post by kanishkdudeja on 2011-07-07
@robert moyse..well sorry..i dont agree with you..i live in India and here ive tried 2-3 data cards..they work perfectly..

---

### Post by adithyajones on 2011-07-07
> **kanishkdudeja said:**
> well..did u install the setup given in the cd?

That crossplatform stuff..

i use reliance netconnect too..

that installer doesnt work for me..

all i did was go to network connections..

under mobile broadband create a new connection..

then select reliance from the subscriber list..

then when they tell you to enter username password..enter it..

and  number is #777

unplug ur reliance netconnect..plus it again..after 2-3 mins..it automatically gets connected and you will be able to use it.

@kanishkdudeja

I did all the steps described above..It is showing that Reliance is connected with network signal and Reliance CDMA written in the network option..But when I open firefox and open a website it is not working..I am using ubuntu11.04 along with windowsxp in a multiboot environment

---

### Post by kanishkdudeja on 2011-07-07
umm..okay..

well..that's pretty strange..does it work fine in windows?

---

### Post by adithyajones on 2011-07-08
> **kanishkdudeja said:**
> umm..okay..

well..that's pretty strange..does it work fine in windows?

@kanishkdudeja

Actually it is searching for network,I thought when I saw Reliance CDMA in the network manager,it got connected..In windows it is working fine..I tried with Idea netsetter following the above steps and it got connected without any issue..In case of Reliance I have to find some other way..

---

### Post by kanishkdudeja on 2011-07-08
by the way..

i just installed ubuntu 11.10 today...

and ran into the same problem..

it did not connect..

but in 11.04 it does connect.

---

### Post by adithyajones on 2011-07-09
Now I am able to connect using Reliance netconnect..I followed the steps mentioned here [http://veerasundar.com/blog/2010/06/how-to-make-reliance-netconnect-broadband-to-work-on-ubuntu-10-04/](http://veerasundar.com/blog/2010/06/how-to-make-reliance-netconnect-broadband-to-work-on-ubuntu-10-04/) .Installed latest 5 debs through synaptic manager and used wvdial and gnome-ppp and it got connected..

---

### Post by kanishkdudeja on 2011-07-09
cool.

i'l see if it works for me in Ubuntu 11.10

please mark the thread as solved so that people don't waste their time looking into your thread as you've already solved it. :)

---

### Post by kpraveenthomas on 2011-08-17
> **adithyajones said:**
> Now I am able to connect using Reliance netconnect..I followed the steps mentioned here [http://veerasundar.com/blog/2010/06/how-to-make-reliance-netconnect-broadband-to-work-on-ubuntu-10-04/](http://veerasundar.com/blog/2010/06/how-to-make-reliance-netconnect-broadband-to-work-on-ubuntu-10-04/) .Installed latest 5 debs through synaptic manager and used wvdial and gnome-ppp and it got connected..
Hi guys, I connected to internet with reliance netconnect with ubuntu 11.04 without an issue. But when the connection remains ideal for a while, the reliance modem disconnects automatically and then connecting it back is becoming a problem, either you have to disconnect the USB and connect back or logout and login back. 

Has anyone noticed this? is there is a solution to this?

---

### Post by kanishkdudeja on 2011-10-21
no idea mate.

---

