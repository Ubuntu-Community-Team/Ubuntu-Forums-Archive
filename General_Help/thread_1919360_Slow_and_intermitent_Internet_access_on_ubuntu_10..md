---
title: "Slow and intermitent Internet access on ubuntu 10.04 64 bits"
date: 2012-02-02
forum: General Help
---

### Post by kokorini on 2012-02-02
Hi. Thank you very much for your help.
I have Ubuntu 10.04 64bits, fresh install

I have this problem. my internet access is slow and intermitent, for example if i ping to google it may start with results and sunddenly stop or not even start. Browsing is the same.

I try by disable the ipv6: if not I do this
cat /proc/sys/net/ipv6/conf/all/disable_ipv6
it returns 1 so it is disable

I tried also using different dns but the problem persist


of course I know my internet connection is ok becouse another computer navigate perfect.

I dont know where to search any more!!
thank you for your help!

---

### Post by Tony1337 on 2012-02-02
Try installing 11.10 if you have a new computer. Newer versions have newer drivers, and sometimes the old ones are faulty/incompatible. When I tried to install 10.04 on my laptop, it would not connect to the internet at all, but everything was fine once I installed 11.10.

---

### Post by kokorini on 2012-02-02
I just tried from the liveCD of the 11.10 and it seems to have the same problem.

thanks for your answer

---

### Post by 3rdalbum on 2012-02-02
Don't have more than one connection active at a time - for instance if you have two wireless cards, only connect one to the network.

What is your internet speed? Ubuntu seems to have problems when using very slow internet connections (128kbps or under)

---

### Post by kokorini on 2012-02-03
"Don't have more than one connection active at a time - for instance if you have two wireless cards, only connect one to the network."

My computer have only the onboard lan.

Some extra info: I just change my computer, the old one is with ubuntu 10.04 32 bits (and windows) working perfect.

about my connection speed, it is 3Mb

I have a LiveCD of a ubuntu 9.10 32bits... I will it from the cd to see what happend.

Thanks!

---

### Post by kokorini on 2012-02-03
Ok... I tried the 9.10 32 bits

In the first moment it seems to work better but not perfect, some how slow (perhaps it is because I was running from the liveCD).

But after a few moments it start to be intermitent again, for example if I ping to anything sooner or later it hangs
or if the ping start without answer it my say something like "host [www.google.com](www.google.com) not found"

I like to say that my other computers navigate perfect and on this computer under windows 7 internet is very well too.


right now I think it may be some driver issue. I have Asus M5A88-M motherboard

thank you you all great community!

---

### Post by varunendra on 2012-02-04
Hi kokorini,

From the problematic computer, please post the outputs of the following:
```
uname -mr
sudo lshw -C network
lsmod
ifconfig
cat /etc/network/interfaces
cat /etc/nsswitch.conf
cat /etc/resolv.conf
ping -c 6 google.com
```Also, do all your computers connect directly to the router or through a switch? Have you tried replacing the cable?


**_EDIT_:**
Please wrap the outputs in [noparse]```
 and 
```[/noparse] tags by clicking on the # symbol at the top of the edit box (in which you create new posts) to generate the tags, then copy-paste the outputs in-between those tags. It preserves the formatting of the output and makes it easily readable.

---

### Post by kokorini on 2012-02-04
In the moment I wrote "I think is the driver" then I search for it a end up with this another thread:

[http://ubuntuforums.org/showthread.php?t=1831870&highlight=M5A88-M](http://ubuntuforums.org/showthread.php?t=1831870&highlight=M5A88-M)

now, with the driver it navigates very well.

thank you people!

---

