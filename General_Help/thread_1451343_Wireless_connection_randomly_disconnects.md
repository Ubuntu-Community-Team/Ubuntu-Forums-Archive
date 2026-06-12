---
title: "Wireless connection randomly disconnects"
date: 2010-04-10
forum: General Help
---

### Post by Shadow12313 on 2010-04-10
I don't know why but for some reason my wireless connection keeps disconnecting and the only way to reconnect it is to unplug my network adapter and plug it back in. As I am writing this my wireless has just disconnected again.  It is really annoying and any help would be greatly appreciated.

---

### Post by cdude42 on 2010-04-10
> **Shadow12313 said:**
> I don't know why but for some reason my wireless connection keeps disconnecting and the only way to reconnect it is to unplug my network adapter and plug it back in. As I am writing this my wireless has just disconnected again.  It is really annoying and any help would be greatly appreciated.

Sme thing happpens to me, im on 10.04. sometimes i can go for several hours, sometimes its only several minutes till i have to unplug and plug it back in.... very annoying.

---

### Post by Shadow12313 on 2010-04-10
I am also on 10.04 but I am not sure if that has anything to do with it.

---

### Post by dslachut on 2010-04-10
it's happening to me on my new Gateway NV5214U laptop.  I can connect to my home wireless network.  It stays connected for a little while and then I can't connect without relogging or restarting.

---

### Post by Shadow12313 on 2010-04-10
Are you also on 10.04 (Lucid Lynx)?

---

### Post by dslachut on 2010-04-10
No, I'm not.  I'm still running 9.10, I didn't see that everyone else was in the thread was on 10.04.  My apologies.  Should I start a new thread, then?

---

### Post by Shadow12313 on 2010-04-10
No it doesn't really matter as long as the problem is solved.

---

### Post by Shadow12313 on 2010-04-12
I would just like to report that my problem has been fixed by changing to a different network adapter.

---

### Post by chrispche on 2010-05-03
How do you do that?

---

### Post by atulkakrana on 2010-05-03
Same here..wifi disconnects after some time..need to restart adapter to reconnect...Its quicker then restarting...I am using Dell studio 14 (i5) with broadcom wifi card...

---

### Post by Shadow12313 on 2010-05-03
> **chrispche said:**
> How do you do that?

You just plug in a different wireless adapter.

---

### Post by xDarkicex on 2010-05-03
Happens to me but only when I have a very weak signal 50% and up I have never had one drop, on 10.04

---

### Post by atulkakrana on 2010-05-04
> **xDarkicex said:**
> Happens to me but only when I have a very weak signal 50% and up I have never had one drop, on 10.04

True. It only disconnects when signal strength is low. I cant change my internal wifi card.

---

### Post by Teh_Messiah on 2010-05-05
I have only just upgraded to Xubuntu 10.04 this morning on my MSI Wind from Xubuntu 9.10.

In 9.10 my wireless worked flawlessly and never dropped but now it doesn't stay connected at all.

It finds the wireless network and sees it but wont connect to it. I have all the same settings from 9.10 but even from the live USB stick i made it wont stay connected.

I'm about to try Ubuntu and also Ubuntu Netbook Remix both 10.04
but i have my doubts it'll change anything.

My phone has stayed in constant connection with the wireless network too so it isn't the Access Point

---

### Post by tommyg562000 on 2010-05-05
I am having the same trouble with ubuntu 10.04. I am using a Linksys wusb54g version 4 wireless adapter. Sometimes it stays connected for long periods sometimes only 10 minutes. I haven't tried unplugging and plugging back in. I just restart the computer.

---

### Post by Teh_Messiah on 2010-05-05
I'm using the built in adapter in my MSI Wind U100 which is a ralink.
I tried Xubuntu 10.04 and 9.04, Ubuntu 10.04 live and Ubuntu Netbook Remix 10.04 and they all failed to stay connected :(

The only one that did stay connected was Win XP!

I reinstalled 10.04 from a usb key alternate i386 edition but no difference.

I'm also having trouble with my Bluetooth connecting to my MS notebook Mouse 5000. There was a command line fix for that but i cant find it anymore :(

About to restart after updateing to new kernel.
BRB

---

### Post by Teh_Messiah on 2010-05-05
Nope, no difference to anything.
Currently installing Bluez for the bluetooth problem but nothing has changed :(

---

### Post by Teh_Messiah on 2010-05-06
Ok I got it working i think.
Both the wireless and the bluetooth!

All I did was click on the networking icon and instead of trying to connect to the visable home wireless that it detected I clicked on the Create New Wireless Network in the drop down menu. Selected the wpa & wpa 2 Personal (my network encription type) typed in the name for my network, and the password and it connected.

As far  as the bluetooth is concerned I'm not sure exactly what i did there but it was alot of messing around and blueman seems a bit dodgy. Mouse is sometimes laggyand takes forever to conect. in my 9.10 it recognised the mouse at the login screen but now i have to wait till i have logged in clicked a few times and wriggled the mouse around for nearly 30 seconds before it does anything :(

I hope this helps someone else out :)

---

### Post by Shadow12313 on 2010-05-06
> **tommyg562000 said:**
> I am having the same trouble with ubuntu 10.04. I am using a Linksys wusb54g version 4 wireless adapter. Sometimes it stays connected for long periods sometimes only 10 minutes. I haven't tried unplugging and plugging back in. I just restart the computer.

That was the same adapter I had problems with.

---

### Post by Teh_Messiah on 2010-05-09
Cancel that, I have had to revert back to Xubuntu 9.10.
The following day it refused to connect and stay connected to the wireless network.
Once i had reinstalled 9.10 it discovered and connected and stayed connected to my wireless net no problems.
I still had problems connecting my bluetooth mouse but after installing blueman and a few extras to bluez it is connected and working.

---

### Post by zainka on 2010-05-21
Hi

Has there been any progress in this topic the last two weeks? 
I have the very same problem using Linksys WUSB54GP (Ver4) adapter. It stay connected for some time, then drop out. "Some time" in this term is from 2 to 4 hours before drop out. Re attaching the dongle will fix the problem.

I am using a clean installation of Ubuntu 10.04, but have had the same problem on 9.10 earlier. 

I have read a few posts where people wants to try different network managers, but is really this the problem? Isn't the managers job just to set up the adapter and then leave it? I would suspect the driver at first, but am unsure which version is installed. 

Since the adapter is using RT2500USB chip-set, I downloaded the source code from Linksys --> [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) . This is version 2.0.8.0 

I have yet not tried to build the driver, but I think this is where one should start. That is if there ain't issues with the network managers I am not aware of and which could cause the connection to drop out periodically. 

[SIZE="1"]Also, Some adapters earlier (some years ago) had this stupid power save function, making the adapter it self disconnecting if it didn't detect any activity for a while or on pure timeout. However, question was always "wath IS activity" and how to turn this "feature" off. I do NOT beleive this is the issue here, but nice to mention anyway if it triggers someone.[/SIZE]

Breg
Vidar

EDIT: I just read some threads about the driver downloaded. It is super old and would prob. not build out of the box. Any suggestions??

---

### Post by Teh_Messiah on 2010-06-07
I haven't tried it again on my laptop. i reverted back to 9.10 since it was reliable for me and stays connected.
I thought it might have been a power saving function at one stage but mine never stayed connected long enough to even consider being idle!
10.04 seems stable so long as there isn't any wireless networking.
I upgraded my old server to 10.04 and through cable it stays connected no worries.
I'm waiting for someone who knows what they are talking about to explain the problem and give us a fix for it!
Until then I am sticking with 9.10!

Sorry Ubuntu team, but no wireless, no install!

---

### Post by zainka on 2010-06-28
I mentioned in my previous post, in small letters, that earlier there where problems similar to this where the wireless dongle put it self into power save mode causing it to loose connection. I also noted that I doubted that this was the case here. "Have no doubt" they say, and that I should have listen to.

iwconfig could tell me that for wlan0, power save mode was set to ON. I just did not pay any attention to that before. After disabling it problem went away. That is, in my case. I guess others may face different problems.

command for turning power monitoring off is
> sudo iwconfig wlan0 power off

For the records, my adapter is WUSB54GP from Linksys and driver used is rt2500usb. Earlier the fix was to reconnect the dongle and reattach to the network.

---

### Post by ilanesh on 2010-07-21
Well I have the same problem on my acer aspire one, 10.04 randomly disconnects, when I start to do something on the internet it disconnects , it stays connected only a few minutes, and this now for weeks, it is unusable when no wireless internet.
With the ohter laptop a Vision Laptop, no such problem, so it has nothing to do with the linksys router.
I have to downlgrade back to 9.10. there I stay alwys connected. Also the powersaving is off.
So I realised all the buntuts with .04 behind have this problem with wireless connections, but not the buntus with the .10, they are all stable. So why not make the .10 buntus a long term support, they are not buggy like the buntus with the .04. Hmmmm, very strange, and even no bug fixings for so long time.:(

---

### Post by santius on 2010-07-25
I have the same problem in Ubuntu 10.04 with an Atheros AR5001 card.

For now the behavior is randomly, and restarting the interface is the only workaround for now.
 
I will wait for updates from Ubuntu, if anyone could fix it, please tell me how!

Thanks

---

### Post by hmjbarbosa on 2010-07-27
Same problem here. Wifi worked flawlessly in 9.04. After upgrading to 10.04 it sucks...  Since I can dual boot into XP and get 100% perfect connect, I am pretty sure the problem does not lie with my hardware (ie wifi card and router).

System info -----

HP Pavillion zv2000
Ubuntu 10.04 (problem with wifi connection)
Windows XP (no problem at all)

Wifi card: 
hbarbosa@arneiroz:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s

---

### Post by claracc on 2010-07-28
I would install wicd to fix the wifi instead of gnome network manager. It is in the repositories.
 
In Karmic Koala if you install wicd with synaptic it uninstall automatically gnome network manager and installs wicd

---

### Post by Spike671 on 2010-07-28
I'm having the same problem with my Asrock Ion 330 although it's really only been happening for about two weeks.  My router is the O2-Thomson TG585v7 and I have no problems with the wifi signal on my laptop which is currently running Vista. 
 
I'll try installing wicd when I get home and see if that helps.

---

### Post by atulkakrana on 2010-08-21
DELL STUDIO 14 + Ubuntu 10.04
Broadcom card
5 Years of power Ubuntu usage
TIME TO MOVE ON ======= WINDOWS 7 Here I come....I want to kiss Bill Gates for first time ever...you have made an incredibly stable system....Windows 7....

The Story 
NO MATTER WHAT I DO MY WIFI DISCONNECTS RANDOMLY....ONLY WHILE DOWNLOADING TORRENTS

Limit speed...turn off Wifi card power saver...Play Rhythmbox to prevent sleep/whatever....etc etc....nothing works...

I am a proponent of linux...i am using it for last 5 years...and when these problems can violently distract me..what will happen to new users....

Canonical and Ubuntu developers...please stop it...you have done enough....do not develop it any more...stop and concentrate on what you have developed already...

I ASSURE YOU THAT ONLY BECAUSE OF THIS PROBLEM>>>I WILL SHIFT TO WINDOWS 7....I personally believe that its easy to use Windows 7 and it is more stable then Ubuntu these days....

GO AWAY UBUNTU...I spend so much of time trouble shooting your problems...still 'full brightness' 'wifi disconnect'  'ALSA re installation after kernel update'....GOD I will shoot myself...Its a GANG BANG..... by Canonical , Ubuntu and Linus torvalds..

I feel sorry but cant help it
Atul Kakrana

---

### Post by Sonsum on 2010-09-02
> **atulkakrana said:**
> DELL STUDIO 14 + Ubuntu 10.04
Broadcom card
5 Years of power Ubuntu usage
TIME TO MOVE ON ======= WINDOWS 7 Here I come....I want to kiss Bill Gates for first time ever...you have made an incredibly stable system....Windows 7....

The Story 
NO MATTER WHAT I DO MY WIFI DISCONNECTS RANDOMLY....ONLY WHILE DOWNLOADING TORRENTS

Limit speed...turn off Wifi card power saver...Play Rhythmbox to prevent sleep/whatever....etc etc....nothing works...

I am a proponent of linux...i am using it for last 5 years...and when these problems can violently distract me..what will happen to new users....

Canonical and Ubuntu developers...please stop it...you have done enough....do not develop it any more...stop and concentrate on what you have developed already...

I ASSURE YOU THAT ONLY BECAUSE OF THIS PROBLEM>>>I WILL SHIFT TO WINDOWS 7....I personally believe that its easy to use Windows 7 and it is more stable then Ubuntu these days....

GO AWAY UBUNTU...I spend so much of time trouble shooting your problems...still 'full brightness' 'wifi disconnect'  'ALSA re installation after kernel update'....GOD I will shoot myself...Its a GANG BANG..... by Canonical , Ubuntu and Linus torvalds..

I feel sorry but cant help it
Atul Kakrana

I'm sorry you have this issue. I hope you realize that people here are just here to help. 

The beautiful thing about Linux is choice. And if your choice is to get Windows 7, that's okay with everybody here.

I just have one question, you said you wanted everyone to "stop developing". Does that mean that this wasn't an issue on a previous Ubuntu release? If so, why can't you use that one?

---

### Post by ulsterman on 2010-09-09
Hi!

I too have had this problem on my Aspire One for several releases now but I have heard that it might be a hardware fault. Can any one confirm if it happens on the original Limpus distro? I won't go back there even for a working wifi. Is this being looked at by the Ubuntu development chaps or is my beloved Aspire One too old?

Ken

---

### Post by cntrational on 2010-11-27
I've been having the same problems. Any updates on a possible solution?

---

### Post by jordanthompson on 2010-12-04
Me too - this is really frustrating.  I have a Dell Studio.

---

### Post by aero13972486 on 2010-12-10
This happened on 9.10 and now on 10.04 with same GSM device: Huawei E180.
I can't not have the internet!
Can someone please say they know what we're talking about and that they're looking into it?

---

### Post by miltonlaufer on 2010-12-19
I have the same problem on a MSI PR310, with atheros

---

### Post by stawek on 2011-01-06
I'm facing similar problems with my Option Globetrotter GSM card (Qualcomm chipset,PCMCIA).
I just installed 10.10 on my notebook few days ago, i can connect and use internet for couple of minutes but it always disconnecting , it's very annoying that i have to reboot my machine to be able to connect again.

I searched over internet for possible solutions and unfortunately found that some people also have this kind of problems with previous versions of ubuntu on various hardware and no solution. I have really old Toshiba Satellite L10 notebook and i think there sohouldn't be problems like this with old hardware (also problems with i855 video card).

I'm sure that it's not my hardware fault - i have opensuse installed also and everything is fine there.

Can someone help me with this problem or there is no solution and should I give up?

Regards.

---

### Post by tbraker on 2011-01-07
Same problem.  Using 10.10 now.  How long has this wireless pcmcia card bug been around???

Google searches lead me to a hodge-podge of fixes.  Mostly ndiswrapper out of band solutions.  Or HUH?, install a windows driver??? Or maybe something about some esoteric network tool that doesn't come with the Ubuntu default Gnome desktop. 

I'll say it: "I should not need to recompile the kernel to maintain my connection to my network"

Who has the answer?  

I'm not busting.  Just frustrated...

Ubuntu is a great OS, but I've been installing this thing off and on for the last 4 years and the SAME *$&# problem exists with the wireless timeout every 10min, maybe 5min, maybe 30min, maybe 30sec...and I can't find out easily through research how to definitively fix it. 

So now I am asking for Chuck Norris' help.

Mr. Norris, please tell the Ubuntu community how we fix this wireless card timeout issue in Ubuntu (whatever distrib)?

Thank you.

---

### Post by maubat63 on 2011-01-25
**Same problem here!**

The connection breaks after a random period of time.

I  am using Ubuntu 9.10 with kernel 2.6.31-22-generic (but also using  Mandriva 2010.0 with kernel 2.6.31.14-desktop-1mnb I have the same  problem).

Wireless adapter is an AirLive WT-2000USB ( **Ralink rt73 chipset** )

The wireless driver is rt73usb from rt2x00.serialmonkey.com project.

Really  the connection behavior is a little bit strange: the connection does  not lost association to access point but ip packets get lost even if you  ping the AP.
The strange thing is that connection already active  (for example player VLC playing streaming internet radio) still goes on  working but you can't get new connection for example surfing web usin  Firefox stops working as you get the message connecting to and then you  get the error page can't connect to.
I work on this assuming that it  was a dns ploblem but it is not because when connection stop working I  can't even ping my access point.

Googling around I found that the  same problem happens to people with different wireless adapter so I  think it may be a problem with new mac80211.

**SOLVED for people using rt73 chipset from Ralink.**

For  people using rt73 chipset from Ralink I get a working well connection  using driver rt73-k2wrlz-source_3.0.3-2~ppa0~karmic_all.deb
from [https://launchpad.net/~marco/+archive/ppa/+sourcepub/908504/+listing-archive-extra](https://launchpad.net/~marco/+archive/ppa/+sourcepub/908504/+listing-archive-extra).

[B]Please read the post on rt2x00.serialmonkey.com support forum for more details.
[/B]
[http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=6118](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=6118)

Good wireless connection to all.

---

### Post by maubat63 on 2011-01-31
**For people using Ubuntu 9.10 and Ralink rt73 wireless adapter!**

I've found that the driver rt73-k2wrlz-source_3.0.3-2~ppa0~karmic_all.deb
from [https://launchpad.net/~marco/+archive/ppa/+sourcepub/908504/+listing-archive-extra](https://launchpad.net/~marco/+archive/ppa/+sourcepub/908504/+listing-archive-extra) is limiting the connection speed at about 2 Mbit per second. :mad:

So I tried the original driver from Ralink corporation at [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

For the chipset rt73 usb the driver is the RT2501USB(RT73:RT2571W/RT2573/RT2671).

It compiles on kernel 2.6.31 found on Ubuntu 9.10 without problem! (just read the instruction).

Read also the comment in the Makefile and comment out the flag for debug this way:

## Comment/uncomment the following line to enable/disable debugging
# EXTRA_CFLAGS += -DDBG

so it will not fill your log with debug information. ;)

**MANUAL CONNECTION**

For Autentication WPAPSK with TKIP you can the use the following command as root in terminal:

ifconfig rausb0 down
dhclient -r rausb0
ifconfig rausb0 up
iwconfig rausb0 essid "your_AP_name"
iwpriv rausb0 set AuthMode=WPAPSK
iwpriv rausb0 set EncrypType=TKIP
iwpriv rausb0 set WPAPSK=your_wpa_key_in_ascii
dhclient rausb0

and you are connected with maximum speed connection and without any loss of connection.

**AUTOMATIC CONNECTION**

You can configure your Ubuntu 9.10 to set up the connection automatically using the driver
config file rt73sta.dat
Just create /etc/Wireless/RT73STA/ and copy there the rt73sta.dat you can find in the driver directory.

mkdir /etc/Wireless
mkdir /etc/Wireless/RT73STA
cp rt73sta.dat /etc/Wireless/RT73STA

then edit the rt73sta.dat changing:

SSID=your_AP_name
AuthMode=WPAPSK
EncrypType=TKIP
WPAPSK=your_wpa_key_ascii

and leaving the rest untouched.

For automatic connection then edit /etc/network/interfaces adding:

iface ralan0 inet dhcp
pre-up iwconfig

Ok now when you boot your Ubuntu you are automatically connected.

Good connection!  ):P

---

### Post by imsangha on 2011-02-07
This Ubuntu wifi problem is driving me up the wall... I don't have this problem anywhere else, but only in Soda hall, UC Berkeley. It must be Ubuntu causing this mess, not my hardware, because wifi works just fine in Windows 7.

It has been extremely frustrating. I've tried installing wicd, removing lm-sensors, and some other methods... None of them ever worked! I've been having this problem the past 3 semesters, and Airbears still keeps throwing me off its wifi network every 30 seconds to 2 minutes.

I can observe this problem on my Macbook, MSI GX660R-US, and Acer netbook with Ubuntu netbook remix installed... Basically on all of my computers. So please keep me posted on this if anyone has a solution.

---

### Post by electroken on 2011-02-07
I wonder is this is in any way related to a problem I am having with my Ubuntu install on a desktop at my home here. I originally was using the network manager which is installed normally with the 10.04 distro disk. Then since I would seem to have it drop out of connection on me, I decided to take some advice and install the one you call Wicd (if I recall name of program correctly) and the ndiswrapper thing. I am told it was supposed to replace the network manager but that seems to still be there. The network manager icon seems to show connection but the Wicd one then tends to show not connected and when I try firefox it goes off line etc. 
It can sometime last for days before going out on me though.
As a try at fixing this I uninstalled the Wicd thing and if I continue to have any issues, I will get it off the program list again and reinstall it. Wish me luck.

---

### Post by imsangha on 2011-03-02
[http://ubuntuforums.org/showthread.php?t=1507732](http://ubuntuforums.org/showthread.php?t=1507732)

Just letting you know, my wireless connection problem has been completely resolved. The link above demonstrates what I did to get rid of the problem. Good luck! :D

---

