---
title: "Old Version"
date: 2010-05-29
forum: General Help
---

### Post by bobrunson on 2010-05-29
I foolishly installed Ubuntu 8.01 from a CD I had from 2 years ago. Installation is fine, dual boot works, but in my first efforts I am unable to access the internet. Can I correct the problem, or is there a way to install a newer version? My ignorance of Ubuntu is obvious, and any help would be deeply appreciated.
Message I get is as follows:
“Firefox is currently in offline mode and can't browse the web.
The browser is currently in the offline mode and cannot connect to the requested item.
Is the computer connected to an active network?  Place the browser in online mode and try again.”
My system:Gateway DX4831, Intel Core i5, [EMAIL="650@3.2GHz"]650@3.2GHz[/EMAIL], 8 GB RAM, 64-bit Windows 7 Professional, DSL wired internet, Speedstream modem
 
I obviously cannot reach Ubuntu help except by rebooting into Windows. Apologies for my ignorance and thanks for any help.

---

### Post by lsutiger on 2010-05-29
#1 how are you connecting to the network? Are you trying wireless or through an ethernet cable?
#2 yes you can install again with anewer version....I have been running 9.04 on my notebook for over a year with nearly no problems.

---

### Post by bobrunson on 2010-05-29
Internet is thru ethernet cable.  How do I update my old version to 9.04?  Remember it will have to use Windows rather than Ubuntu.  Thanks for the help.

---

### Post by lsutiger on 2010-05-29
OK. 
Are you directly connected to a router or to a modem?

Could you post the result of : ifconfig

---

### Post by quadproc on 2010-05-29
> **bobrunson said:**
> I foolishly installed Ubuntu 8.01 from a CD I had from 2 years ago. Installation is fine, dual boot works, but in my first efforts I am unable to access the internet. Can I correct the problem, or is there a way to install a newer version? 

Assuming that you actually meant version 8.10, I used that version for some time without any Internet accessibility problems so yes, it is capable of working.

The error messages that you quoted are indicative of the network not being available.  What does your network interface consist of (NIC, firewall if any, Ethernet cable, wireless link, switch, router, modem?  Do you use DHPC or fixed IP address?  Can you ping anything from your system?

quadproc

---

### Post by oleink on 2010-05-29
> **bobrunson said:**
> Internet is thru ethernet cable.  How do I update my old version to 9.04?  Remember it will have to use Windows rather than Ubuntu.  Thanks for the help.

Well there are two routes (I suggest the 2nd)

1) you can use the update manager (but you will need internet for this #1 and #2 I don't suggest it unless you want to do a fresh install every other release which is what I do)

2) Use gparted and remove the ubuntu partition completely and then install (from a cd that you can burn of 10.04) the new ubuntu version where it was or expand the windows partition over the ubuntu one and then install the same way you originally did (well at least i expect you did- by having ubuntu take up about half maybe less of the hard drive)

---

### Post by bobrunson on 2010-05-30
Apologies for the delay, but thanks for the suggestions.  This afternoon I made a 9.04 ISO disk and tried it as a live CD.  I get the same message about Firefox.  As to your questions/suggestions:
isutiger-- I am directly connected with ethernet cable to Speedstream modem.
quadproc-- ethernet cable modem, Norton Internet Security Firewall, presume a fixed IP address, don't know how to ping.
oleink: Can't try #1 without internet connection.  Reading forums makes me think removing ubuntu partition changes the boot file and would leave me with an unbootable machine.
 
Again, I thank you for the help but am seriously considering restoring from a disk image and passing up Linux as too complicated for me.

---

### Post by oleink on 2010-05-30
> **bobrunson said:**
> Apologies for the delay, but thanks for the suggestions.  This afternoon I made a 9.04 ISO disk and tried it as a live CD.  I get the same message about Firefox.  As to your questions/suggestions:
isutiger-- I am directly connected with ethernet cable to Speedstream modem.
quadproc-- ethernet cable modem, Norton Internet Security Firewall, presume a fixed IP address, don't know how to ping.
oleink: Can't try #1 without internet connection.  Reading forums makes me think removing ubuntu partition changes the boot file and would leave me with an unbootable machine.
 
Again, I thank you for the help but am seriously considering restoring from a disk image and passing up Linux as too complicated for me.

You don't have to give up.  I had a really hard time when I first started out.

---

### Post by quadproc on 2010-05-31
> **bobrunson said:**
> Apologies for the delay, but thanks for the suggestions....
No problem.  I completely understand about not being able to get to the forums for whatever reason.> 
quadproc-- ethernet cable modem, Norton Internet Security Firewall, presume a fixed IP address, don't know how to ping.
OK, I think I understand your setup.  Presumably the Norton software is on a Windows installation?  You do not generally need any firewall software in Ubuntu unless one of two things is true: 1. You are running a server, or 2. You have explicitly enabled one or more Internet ports.  If the Norton is present on the Ubuntu system then I would suggest removing it since it could be in your way.

Another question that I should have asked: are you using a proxy?  If so then check that to be sure that its setup is correct.

A very brief intro to ping: the ```
ping
``` command can be typed into a terminal window along with an IP address and will send test packets of data to that address.  Your modem probably has an IP address of its own; its manual should tell you what it is.  IP addresses of the original type consist of 4 numeric values separated by dots (later IP addresses consist of 6 values).  For local area nets (LANs) these will start with 192.168 so a typical modem might have an address of 192.168.0.1, for example.  If your modem doesn't have an IP address then it will furnish the IP address of whatever is on the other end of the connection.

IP addresses may change from connection to connection.  If your IP address is fixed then it won't but if you are using DHCP then a new address may be used on every connection.  DHCP is generally the most popular.

To learn a bit more about your particular Internet setup, type ```
ifconfig
``` into a terminal window.  This will report a few lines of interesting things about your computer's setup.  You could copy that information into a reply post here and someone could tell you what it indicates.

So, to ping your modem (and assuming that the modem is at 192.168.0.1) you would type ```
ping 192.168.0.1
```into a terminal window.  This will start a process which periodically pings the specified IP address; to stop the process; type control-C. If ping works then you know that the hardware (including cables) is working between your computer and the thing that you pinged.  Ping is a very low level thing; actual messages depend on several additional things being correctly set up and functioning correctly but if ping works then you know that part of the hardware/software is good.
> 

Again, I thank you for the help but am seriously considering restoring from a disk image and passing up Linux as too complicated for me.Please don't be discouraged.  You are undertaking a new endeavor and there is an initial threshold to overcome; it may seem to be overwhelming but as you use the system it will become familiar and easy.  And there are lots of people here who can and will help.

I personally will not be around for a day or more after today but I am sure that others will offer help if they read your postings.

quadproc

---

### Post by WinRiddance on 2010-05-31
**Usually the newer the system, the more it'll work in your favor.** You need to realize that the Ubutu developers push out a new release every 6 months. That's the schedule and has been for some time, every 6 months a new release ... as opposed to 5 or 6 years with Windows (XP to Vista). Consequently it's generally better for the "uncomfortable new Ubuntu user" to install the latest and greatest Ubuntu (currently version 10.04) as opposed to a version that's already had 3 releases since the one that you're were using (8.10).

**Here's what I would suggest** since you already stated that you have an internet connection with an ethernet cable which means that you don't have to do anything critically important within 24 hours time since your dual-boot setup still appears to be working as well.

First I'd recommend replacing the installed default network manager by **wicd** instead. Wicd is more user friendly and has worked "miracles" on some older machines and even newer ones with WiFi connection issues (our Sons year old laptop being one of them). You can install wicd by copying and pasting this code into your terminal:
(you'll be asked to supply your password anytime that you enter a "sudo" command)

```
sudo apt-get install wicd
```[I]

Now go ahead and remove the ethernet cable, followed by logging out. Then log back in and you should have the wicd symbol in your START MENU ... INTERNET location. Open it up by clicking on it and then try REFRESH to see if it will pick up your WiFi signal. If I remember correctly this will not work if the ethernet cable is still attached. If your WiFi network is located you may or may not need to set that network up properly first, with either a key phrase or a network key. But this is standard for WiFi under Windows too. If you still can't get it working re-attach the ethernet cable, wait a few seconds, then refresh wicd again.

There's also help available with the current Ubuntu 9.04 that you're using and the Firefox Flashplayer plugins. Just go to this page here, very simple instructions, copying some code one time into the terminal.
[http://geek.joshwaihi.com/content/adobe-flash-plugin-firefox-ubuntu-jaunty](http://geek.joshwaihi.com/content/adobe-flash-plugin-firefox-ubuntu-jaunty)

Believe me, Ubuntu is so incredible to use and have, in my opinion by far easier yet even more comprehensive than Windows. **You just have to give yourself a little time** and not become discouraged right away. There's no comparison between Ubuntu 8.10 and 10.04. When you used Windows for the very first time (or Mac) everything had to be gotten used to at first as well. Just be willing to spend a little time here and you'll see that there are solutions available. I know seniors that have switched to Ubuntu and they're loving it. Gotta have a little patience though, that's all there's to it. You'll love Ubuntu just like everybody else who gets involved with it.
[/I]

---

### Post by bobrunson on 2010-05-31
WinRiddance:  I will work on it, and thank you for the suggestions and encouragement.  Just give me a little time, and I will report on the results

---

### Post by bobrunson on 2010-05-31
quadproc:  Thank you for the help and encouragement.  You have given me much to work on and I shall keep trying.  At the moment my wife reminds me that today is my 89th birthday and says to get off the machine!

---

### Post by clarkkillick on 2010-09-01
Hello bobrunson,

I just stumbled into this thread, and see that you've been given some strange replies.  I think your problem connecting to the 'net is to do with the Speedstream modem.  My own experience is with a D-Link ADSL Modem that connected to the PC via an Ethernet cable.  This worked with some Linux versions but not others.

You mentioned a "cable modem" - I assume that you mean something similar to my old D-Link, as you also called it "DSL".  A 'real' cable modem is for getting broadband over fibre-optic cable.

I hassled with the D-Link and got it to work in Ubuntu, but I became much more satisfied when I replaced it with a proper router, which works with all the different Linux versions that I use.  I've used a Siemens router (I forget which model), and I'm currently using a Netgear DG834G.

When you first connect a router you need to configure it; normally you log on to its configuration screen and set your broadband username and password, or you can use the router's 'installation CD' in Windows.  After that, the router handles connection to ADSL automatically, and your Windows or Ubuntu system just uses it as a 'gateway' to the Internet via an Ethernet cable.

---

