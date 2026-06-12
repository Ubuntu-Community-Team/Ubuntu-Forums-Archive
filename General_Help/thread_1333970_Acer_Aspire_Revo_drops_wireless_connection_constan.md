---
title: "Acer Aspire Revo drops wireless connection constantly!"
date: 2009-11-22
forum: General Help
---

### Post by agro666 on 2009-11-22
Nettop = Acer Aspire Revo w/ 802.11n internal, Ubuntu 9.10
Router = Buffalo WHR-G300N.  Modded to use high gain external antennas and running DD-WRT.
Laptop = Lenovo T61 (internal 802.11g) WinXP
Desktop = 100Mbit, Win 7

Revo is connected 802.11n, laptop is connected 802.11g.  Desktop is ethernet to the router 100Mbit.

Downstairs with my laptop about 10 feet from the Revo, if I wirelessly SFTP to my desktop, I get a sustained 2200KB/sec.  That seems good for 802.11g, right?

Downstairs with the Acer Revo, if I wirelessly SFTP to my desktop, I get about 1500KB for 1-2 second and then the wireless drops on the Revo.  It reconnects, but I always drop when I attempt to transfer a large file sustained.

What recommendation would you guys have in order to troubleshoot this?  I dont know if it has to do with Linux drivers and the Revo?  Should I somehow try to force the Revo to 802.11g and see if it is stable?  How can I go about doing this in Ubuntu?  What more information can (and how) I provide you guys so I can help you help me? :)

I found a few things that seemed interesting:

revo@Revo:/proc/net$ cat wireless 
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
 wlan0: 0000   27.  -83.  -256        0      0      0      0      0        0

revo@Revo:/proc/net$ cat dev
Inter-|   Receive                                                |  Transmit
 face |bytes    packets errs drop fifo frame compressed multicast|bytes    packets errs drop fifo colls carrier compressed
    lo:   17576     137    0    0    0     0          0         0    17576     137    0    0    0     0       0          0
  eth0:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0
wmaster0:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0
 wlan0:1551680813 1796997    0    0    0     0          0         0 59827571  548177    0    0    0     0       0          0

wlan0     Link encap:Ethernet  HWaddr 0c:60:76:42:45:57  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e60:76ff:fe42:4557/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1797019 errors:0 dropped:0 overruns:0 frame:0
          TX packets:548188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1551682986 (1.5 GB)  TX bytes:59829597 (59.8 MB)

---

### Post by spcwingo on 2009-11-22
I used to have problems similar to this with gnome network manager on my wife's laptop.  I just replaced it with WICD.  I think you can install it from the repos since Intrepid (not quite sure as I'm still on Hardy).

---

### Post by agro666 on 2009-11-22
Thank you!
That was definitely a move in the right direction.  I still have some instability, but I may play with the channels and such.  I was able to do 20-30 seconds of transfers before getting a hiccup.

My new big badass high gain antennas should be here Monday, that may help too.  I may also relocate the revo so its closer and not near all my electrical mumbo jumbo.

Good call on that.  Thank you!

---

### Post by grmmog on 2009-12-03
Having the same problems with my Revo 3610 as well.  The network connection is consistently buggy.  It'll drop packets during ping tests and ssh is barely usable at times.

My router is WRT310N using dd-wrt.

---

### Post by agro666 on 2009-12-03
> **grmmog said:**
> Having the same problems with my Revo 3610 as well.  The network connection is consistently buggy.  It'll drop packets during ping tests and ssh is barely usable at times.

My router is WRT310N using dd-wrt.

I never did get a solution.  I am thinking that the built-in wireless antenna just may be a piece of crap.

I ended up using another router and having it be a client bridge to my main router.  I then plug the revo & my tivoHD in to the client bridge and use that wireless instead.   not ideal, but it works.

---

### Post by redoranges on 2010-01-31
I'm having the same problem, can anyone think of how to solve this?

---

### Post by antlfgrnd on 2010-02-12
I have an Aspire Revo 3610 and I'm having the same issue.  I have spent a great deal of time attempting to find the root cause with no luck.  Can someone shed some light on this issue, or offer some guidance on where to start the diagnosis?  

Thanks in advance.

---

### Post by SiliconS on 2010-02-15
This worked for me: [http://ubuntuforums.org/showthread.php?t=1378485](http://ubuntuforums.org/showthread.php?t=1378485)

---

### Post by graabein on 2011-01-25
> **spcwingo said:**
> I used to have problems similar to this with gnome network manager on my wife's laptop.  I just replaced it with WICD.  I think you can install it from the repos since Intrepid (not quite sure as I'm still on Hardy).

How do I replace it? I've managed to install WCID but now they're both running (without a logout/restart).

---

### Post by redmaniac on 2011-06-23
Hi all,

in case some other people have issues with this:

I have an Acer Apsire Revo r3700. I experienced some WiFi issues, namely that the connection would drop sometimes (however not often enough to be more than a nuisance). In addition the signal was always unusually weak and would fluctuate constantly. My apple sitting right next to my revo had not trouble whatsoever and my old machine using a usb wifi stick was also fine with the signal. 

What helped me is to disable bluetooth. Now this will not work for people who want to use their revo as a media pc and want to surf from the couch. But in case you use it as a home server or as a small desktop machine (as I do) it might help.

cheers

redmaniac

---

### Post by redmaniac on 2011-06-24
> **redmaniac said:**
> Hi all,

in case some other people have issues with this:

I have an Acer Apsire Revo r3700. I experienced some WiFi issues, namely that the connection would drop sometimes (however not often enough to be more than a nuisance). In addition the signal was always unusually weak and would fluctuate constantly. My apple sitting right next to my revo had not trouble whatsoever and my old machine using a usb wifi stick was also fine with the signal. 

What helped me is to disable bluetooth. Now this will not work for people who want to use their revo as a media pc and want to surf from the couch. But in case you use it as a home server or as a small desktop machine (as I do) it might help.

cheers

redmaniac

I spoke too soon. Disabling bluetooth did make it a little better but it definitely did not solve the problem. I might try and compile a newer version of the driver from the Ralink website. If I do I will post the results.

---

### Post by redmaniac on 2011-06-25
Ok, I've tried compiling the driver and it doesn't work out of the box. I get some compile error in cfg80211.c. No idea where that comes from and I don't want to get into debugging this code. 
This strikes me as odd though.. according to this[ http://ubuntuforums.org/showpost.php?p=10570020&postcount=133]("http://ubuntuforums.org/showpost.php?p=10570020&postcount=133") one can simply follow the instructions mentioned at the beginning of that thread to compile the 3090 driver. If one believes the date of the post and the date of publication of the driver on Ralink's website the lucky fellow in the above post should have used the same version of the driver as me.

---

