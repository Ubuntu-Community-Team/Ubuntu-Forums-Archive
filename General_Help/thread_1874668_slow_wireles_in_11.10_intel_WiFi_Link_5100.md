---
title: "slow wireles in 11.10 intel WiFi Link 5100"
date: 2011-11-03
forum: General Help
---

### Post by cloyd on 2011-11-03
I've searched just about everywhere I can think of, and still can't find a solution. Just upgraded to (not a fresh install, but upgrade from 11.04) to 11.10. Wireless was good on last version. In 11.10, wireless is so slow as to be useless. (Currently using a wired connection). It worked great with 11.04. I've tried this:

                                 [B]echo "#disable ipv6" | sudo tee -a /etc/sysctl.conf
echo "net.ipv6.conf.all.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
echo "net.ipv6.conf.default.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
echo "net.ipv6.conf.lo.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf[/B]
 Then restart  system.
 This didn't work.


I've tried booting on previous kernels. That didn't help.


In the past, on my older netbook, wireless backports seemed to help. Those don't seem to be available here.



This machine has been very good on every version of Ubuntu since 9.10.  The Wireless card is a Intell WiFi Link 5100.  Sysinfo also gives: Subsystem Intell Corporation WiFi Link 5100AGW.


I like 11.10. I need wireless.

 
Help would be appreciated.
Thanks in advance.

---

### Post by cloyd on 2011-11-03
It looks like I've found a crude workaround that won't work for everyone. I downloaded an android app on my phone that allows wired tethering to the computer. I turned off the mobile network on the phone . . . it is using the house wifi and not the phone's mobile network (that could get expensive). . , and it works fine as a wired connection.  

WiFi hotspot for phone is not enabled. 

Name of the app is Auto Tethering.

The phone is not rooted.

This is not solved, but I am not desperate. 

Still wish for a real solution.

---

### Post by cloyd on 2011-11-04
bump

---

### Post by cloyd on 2011-11-05
bump

---

### Post by bobd72 on 2011-11-06
Sorry I am unable to offer a solution - I have exactly the same problem.  Toshiba laptop worked fine in 11.04 but is now so slow as to be almost unusable. Intel 5100 wifi.   File transfers take forever. Aggghhh!

---

### Post by cloyd on 2011-11-06
Ok. So it seems to be tied to our wireless cards. I've never messed with proprietary drivers, but this does tell me I may need to go in that direction. I guess time to study up on using windows drivers in ubuntu.  I'll do some digging later. If anyone has any suggestions on how to go, let me know. Thanks for the reply.

---

### Post by clrg on 2011-11-06
You can try installing the latest wireless driver version:

[http://linuxwireless.org/en/users/Download#Download_latest_Linux_wireless_drivers](http://linuxwireless.org/en/users/Download#Download_latest_Linux_wireless_drivers)

---

### Post by cloyd on 2011-11-06
Will look at this this afternoon  . . .  going to be away from my computer for a few hours. Thanks.

---

### Post by gandaran on 2011-11-06
try changing the router security mode
some Intel wireless drivers have problems with some security modes.

---

### Post by hj1852 on 2011-11-06
I had this same problem; tried disabling ipv6, didn't help at all. Then I tried this:

Open a terminal and enter

```
**sudo -s**
**gksu gedit /etc/modprobe.d/ath9k.conf**
```

At the end of the file enter

```
**[B]options ath9k nohwcrypt=1**[/B]
```

Save and restart.

I found this answer at [http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1785-resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1785-resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal) , the above solution is the second fix.

---

### Post by gandaran on 2011-11-06
> **hj1852 said:**
> I had this same problem; tried disabling ipv6, didn't help at all. Then I tried this:

Open a terminal and enter

```
**sudo -s**
**gksu gedit /etc/modprobe.d/ath9k.conf**
```

At the end of the file enter

```
**[B]options ath9k nohwcrypt=1**[/B]
```

Save and restart.

I found this answer at [http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1785-resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1785-resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal) , the above solution is the second fix.
what the atheros ath9k driver got to do with Intel drivers?

---

### Post by cloyd on 2011-11-08
sorry about that. Perhaps the mods can remove this post.  When things are slow, I sometimes press too many buttons. Doesn't help a bit.

---

### Post by cloyd on 2011-11-08
Still no go.  Some more information and a bit of history.  The machine is a 64 bit machine running on a 32bit pae kernel in order to utilize 4gig of ram (don't know that I've ever needed 4 gig of ram, but I've got it). The first thing I did was to enable backports, yet no backports for wireless were listed. I loaded a windows driver (NETwNx32). Wireless showed up strong panel, but did not work at all.  I did not disable old drivers (didn't really know how). In addition, if I disable old drivers, how do I enable them if I must? 

Still working.

---

### Post by cloyd on 2011-11-08
Got it!!!!!

I found it here:     [http://kjeldahl.net/d7/node/30](http://kjeldahl.net/d7/node/30)

in a paragraph about 2/3 down the page. Really, at the bottom of the page. It is the last paragraph before a comments section. I'll copy it here.

"**Atheros wireless drivers:** This one seems to be haunting  Linux. For older type cards (lspci outputs "Intel Corporation Ultimate N  WiFi Link 5300") it seems the full series of Oneiric alphas, and betas  so far, has a regression as far as cryptography in the "iwlagn" driver  goes. To work around it and get decent wifi speed again, add "options  iwlagn swcrypto=1" to /etc/modprobe.d/iwlagn.conf . For newer cards, add  "options ath9k nohwcrypt=1" if you're having really slow wifi.  Hopefully these will be nailed (again) before the final Oneiric release."

Note that the passage starts talking about Atheros drivers, but then talks about intel drivers.

I had to create the config file . . . it did not exist in /etc/modprobe.d. This one line is the content of the config file. Also had to start gedit with sudo because couldn't save the file without sudo.

Hope this works for someone else.

---

### Post by jaley_ on 2011-11-09
> **cloyd said:**
> Got it!!!!!

I found it here:     [http://kjeldahl.net/d7/node/30](http://kjeldahl.net/d7/node/30)

in a paragraph about 2/3 down the page. Really, at the bottom of the page. It is the last paragraph before a comments section. I'll copy it here.

"**Atheros wireless drivers:** This one seems to be haunting  Linux. For older type cards (lspci outputs "Intel Corporation Ultimate N  WiFi Link 5300") it seems the full series of Oneiric alphas, and betas  so far, has a regression as far as cryptography in the "iwlagn" driver  goes. To work around it and get decent wifi speed again, add "options  iwlagn swcrypto=1" to /etc/modprobe.d/iwlagn.conf . For newer cards, add  "options ath9k nohwcrypt=1" if you're having really slow wifi.  Hopefully these will be nailed (again) before the final Oneiric release."

Note that the passage starts talking about Atheros drivers, but then talks about intel drivers.

I had to create the config file . . . it did not exist in /etc/modprobe.d. This one line is the content of the config file. Also had to start gedit with sudo because couldn't save the file without sudo.

Hope this works for someone else.

Hi,

I'm not actually an Ubuntu user myself so don't take my advice too seriously! :) I fixed this for my girlfriend last night as she uses it on her laptop. I actually added the line:

```
iwlagn swcrypto=1
```

to the end of [FONT="Courier New"]/etc/modules[/FONT] for her as I saw some comments in that file indicating that it would work. Clearly, that's an equivalent work-around to cloyd's above, but I just thought I'd mention that it also works as I've no idea which is the preferred method though!



James.

---

