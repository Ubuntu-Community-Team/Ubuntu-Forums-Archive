---
title: "Not able to connect to internet in ubuntu 10.04"
date: 2011-10-01
forum: General Help
---

### Post by Praveen30 on 2011-10-01
i am using ubuntu 10.04.i have installed ubuntu under windows using wubi.i use datacard to connect to internet.i am facing very unique kind of problem(i think so!!).i am not able to directly connect to internet in ubuntu.But i found a very strange solution, first of all i have to switch to windows,i connect to internet there, then i restart my laptop, switch to ubuntu and i found my net is connected in ubuntu(sounds horrible, i know!).Please and please tell me some solutions..this strange solution is very annoying!!!


I tried both these steps giving on this page but nothing worked-

[http://veerasundar.com/blog/2010/06/how-to-make-reliance-netconnect-broadband-to-work-on-ubuntu-10-04/](http://veerasundar.com/blog/2010/06/how-to-make-reliance-netconnect-broadband-to-work-on-ubuntu-10-04/)

---

### Post by carranty on 2011-10-01
I'm confused by what you mean by *"I have installed ubuntu under windows using wine".* Do you mean you are using wubi?  Or are you dual booting both Windows and Ubuntu?  Are you trying to connect via wireless or a direct ethernet connection?

---

### Post by carranty on 2011-10-01
When you are connected, open a terminal, Applications > Accesories > terminal and type 

[I]ifconfig

[/I]Copy and paste the results to this thread and I might be able to suggest something.

---

### Post by Praveen30 on 2011-10-01
> **carranty said:**
> When you are connected, open a terminal, Applications > Accesories > terminal and type 

[I]ifconfig

[/I]Copy and paste the results to this thread and I might be able to suggest something.

I am so sorry for my mistake.i wrote 'wine' in place of wubi.

well, this is what i got-
```

praveen@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:ae:35:7b:0f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:115.241.139.156  P-t-P:220.224.141.129  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:1 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:10938 (10.9 KB)  TX bytes:3753 (3.7 KB)

```

---

### Post by carranty on 2011-10-01
Hmm, so from the looks of it your using ppp0 as your connection (since this has the most transmitted (TX) and recieved (RX) bytes of data).  I'm not sure what this is though, all of my computers always have eth0, lo and wlan0 not ppp0.  This appears to be the problem though as its saying you have an error.  I'm afraid I can't be of much help because I'm not familiar with wubi and I'm pretty sure this is a wubi issue, perhaps create a new post in the 'Network and wireless' section, this time with a [Wubi] prefix not [Ubuntu].  Hopefully someone else more familiar can help.

If that fails, I'd suggest trying the live cd of ubuntu and see if you can access the internet on that.  If that works at least you know its wubi and not ubuntu, then maybe take the plunge and do a full install??  I've been dual booting windows and ubuntu for years now without issue (so long as windows is installed first!).

Sorry I can't be of more help.

---

### Post by carranty on 2011-10-01
If you do get to the bottom of it please pm me the solution (or a link to it), I'd be interested to know how to resolve it.

---

### Post by Praveen30 on 2011-10-01
> **carranty said:**
> Hmm, so from the looks of it your using ppp0 as your connection (since this has the most transmitted (TX) and recieved (RX) bytes of data).  I'm not sure what this is though, all of my computers always have eth0, lo and wlan0 not ppp0.  This appears to be the problem though as its saying you have an error.  I'm afraid I can't be of much help because I'm not familiar with wubi and I'm pretty sure this is a wubi issue, perhaps create a new post in the 'Network and wireless' section, this time with a [Wubi] prefix not [Ubuntu].  Hopefully someone else more familiar can help.

If that fails, I'd suggest trying the live cd of ubuntu and see if you can access the internet on that.  If that works at least you know its wubi and not ubuntu, then maybe take the plunge and do a full install??  I've been dual booting windows and ubuntu for years now without issue (so long as windows is installed first!).

Sorry I can't be of more help.

The ppp0 because of the mobile broadband connection.I am using datacard or modem(whatever the name)..and i think this is not a problem of wubi because earlier i was using 11.04 version and my datacard was working fine on linux.because of some problem i had to switch to ubuntu 10.04 and from the first day i am not able to connect in it..but i am very desperate to find a solution but don't know what to do..

---

### Post by gandaran on 2011-10-01
> But i found a very strange solution, first of all i have to switch to windows,i connect to internet there, then i restart my laptop, switch to ubuntu and i found my net is connected in ubuntu(sounds horrible, i know!).
I can only think this happens it's probably because the modem remains connected to internet provider while you reboot.
what you should do is check that you have the correct login details required by the mobile internet provider in the setup connection.

---

### Post by gandaran on 2011-10-01
> because of some problem i had to switch to ubuntu 10.04 and from the first day i am not able to connect in it..but i am very desperate to find a solution but don't know what to do..
did you install usb-modeswitch? this package is not installed by default on ubuntu 10.04 as it is on 11.04.
if the modem worked on 11.04 it'll also work on 10.04, the only deference is that on 11.04 it has a list of internet providers info more up to date so the login details (like APN) could be wrong, that's one thing you have to figure out and correct.

---

### Post by Praveen30 on 2011-10-01
> **gandaran said:**
> did you install usb-modeswitch? this package is not installed by default on ubuntu 10.04 as it is on 11.04.
if the modem worked on 11.04 it'll also work on 10.04, the only deference is that on 11.04 it has a list of internet providers info more up to date so the login details (like APN) could be wrong, that's one thing you have to figure out and correct.

i haven't installed it yet.i am going to look for it.well, as far as connection setting is concerned i just have to provide password, username and number for depends on gsm or cdma.These all are correct!!!

---

### Post by Praveen30 on 2011-10-01
> **gandaran said:**
> did you install usb-modeswitch? this package is not installed by default on ubuntu 10.04 as it is on 11.04.


I installed it now what should i do???

---

### Post by Praveen30 on 2011-10-01
spent about 6-7hours but finally it is working!!! finally i will get some nice sleep. i tried everything giving on this page-

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer?action=show&redirect=wvdial](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer?action=show&redirect=wvdial)-

---

### Post by gandaran on 2011-10-01
> **Praveen30 said:**
> spent about 6-7hours but finally it is working!!! finally i will get some nice sleep. i tried everything giving on this page-

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer?action=show&redirect=wvdial](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer?action=show&redirect=wvdial)-
I think you should explain how you asked for mobile broadband help and then you posted a link on dial-up that helped fix the problem which are completely different ways to connect to internet so to help anyone searching for the same problem you should provide more info on the data card/internet provider and what steps you did to make it work.

---

### Post by Praveen30 on 2011-10-02
> **gandaran said:**
> I think you should explain how you asked for mobile broadband help and then you posted a link on dial-up that helped fix the problem which are completely different ways to connect to internet so to help anyone searching for the same problem you should provide more info on the data card/internet provider and what steps you did to make it work.

sorry if i was not clear in my statement.I will try my best to explain it.

device- huawei mobile broadband EC150
After some googling, i got to know this is a particular problem in ubuntu 10.04 and you must have to install
usb-modeswitch to make it work(as gandaran suggested).
In ubuntu 11.04 it is not required and you can connect to internet without any problem.

why to use usb-modeswitch??
I googled a bit and this is what i found- 
[http://linuxers.org/howto/how-set-tata-photon-huawei-ec1261-ubuntu-1004-lucid-lynx](http://linuxers.org/howto/how-set-tata-photon-huawei-ec1261-ubuntu-1004-lucid-lynx)

--->Why i gave that link??
Well, actually with the device i had been given a guide in which it was explained how to connect to  internet using this device( that was pon/poff method, given on that page).it didn't work for me.and earlier i tried one more method 'gnome-ppp', that method is also given on that page. So i thought it was a great compilation of every possible methods to try for.

--->what worked for me??
Because i am not using wvdial or gnome-ppp method to connect. i can say..install usb-modeswitch and complete your network settiings.after that restart your pc/laptop and i hope you will be good to go!!!


I

---

