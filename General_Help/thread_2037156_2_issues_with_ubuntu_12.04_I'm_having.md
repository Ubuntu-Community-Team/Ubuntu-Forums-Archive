---
title: "2 issues with ubuntu 12.04 I'm having"
date: 2012-08-03
forum: General Help
---

### Post by Lithum on 2012-08-03
Hi there, I tried getting ubuntu to recognize my NVIDIA GeForce GT 520MX; Optimus  card so i could enjoy some 3d effects plus it would boost the overall gaming experiance i would be able to have.

Problem is though when i tried to install a nvidia driver yesterday ubuntu got stuck in 640 x 480 resolution.. after a few hours of annoyance and browsing the forums i finally came across with a solution that i entered into the terminal.

However though it still doesn't solve the overall issue of getting my Nvidia graphics card recognized.

Second issue is that I'm also having trouble getting my wireless to work it will connect to the router but it seems that the router or *something* is preventing a connection. I read the windows wireless drivers may of be help, but I tried that out for it only to fail as well.

If anyone could help me out in solving these issues it would greatly appreciated.

-Lithum

---

### Post by Lupajz on 2012-08-03
For that optimus card support you have to check and install Bumblebee 

```
http://bumblebee-project.org/install.html#Ubuntu
```

after install run : 

```
optirun glxgears
```

or 

```
glxgears
```

to see the diference :)

---

### Post by Dylan1473 on 2012-08-03
What type of wireless adapter? And are you using Gnome Network Manager to connect?

---

### Post by Lithum on 2012-08-03
> **Lupajz said:**
> For that optimus card support you have to check and install Bumblebee 

```
http://bumblebee-project.org/install.html#Ubuntu
```

after install run : 

```
optirun glxgears
```

or 

```
glxgears
```

to see the diference :)

alright i'm seeing a graphical difference now, but it has a blank where is should be showing the GPu and heres a paste from terminal when i tried to run glxgears

```

kyle@kyle-300V3A-300V4A-300V5A-200A4B-200A5B:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
kyle@kyle-300V3A-300V4A-300V5A-200A4B-200A5B:~$ optirun glxgears
optirun: command not found

```

---

### Post by Lithum on 2012-08-03
> **Dylan1473 said:**
> What type of wireless adapter? And are you using Gnome Network Manager to connect?

Not too sure what kinda of adapter i have, and i've had this problem in both gnome and unity i just used the defaults that came with the system .. network connections?

---

### Post by Dylan1473 on 2012-08-03
You're probably using Gnome Network Manager then. You could try downloading and using wicd, that's a cross platform one I've used pretty successfully in the past. The only problems I have with it are that it doesn't seem to support VPNs or using multiple wireless network adapters.

First though, can you open a terminal and type

```
lspci | grep Network
```if you have an internal network adapter or

```
lsusb | grep Network
```if you have an external one, then post the output here?

---

### Post by Lithum on 2012-08-03
> **Dylan1473 said:**
> You're probably using Gnome Network Manager then. You could try downloading and using wicd, that's a cross platform one I've used pretty successfully in the past. The only problems I have with it are that it doesn't seem to support VPNs or using multiple wireless network adapters.

First though, can you open a terminal and type

```
lspci | grep Network
```if you have an internal network adapter or

```
lsusb | grep Network
```if you have an external one, then post the output here?

```

kyle@kyle-300V3A-300V4A-300V5A-200A4B-200A5B:~$ lspci | grep Network
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 130 (rev 34)

```

---

### Post by Dylan1473 on 2012-08-03
A Google search with those wireless drivers turns up a lot of people having problems. Not good.

Okay - what happens when you connect to your network? It says you're connected but you don't have internet, right? What happens if you type

```
ping [YOUR ROUTER IP]
```when connected to the network? If you're not sure, your router IP is probably either 192.168.1.1 or 192.168.0.1, and can be found by typing

```
sudo route -n
```and looking next to 0.0.0.0 under Gateway.

And what if you type

```
ping 8.8.4.4
```anything?

---

### Post by Lithum on 2012-08-03
> **Dylan1473 said:**
> A Google search with those wireless drivers turns up a lot of people having problems. Not good.

Okay - what happens when you connect to your network? It says you're connected but you don't have internet, right? What happens if you type

```
ping [YOUR ROUTER IP]
```when connected to the network? If you're not sure, your router IP is probably either 192.168.1.1 or 192.168.0.1, and can be found by typing

```
sudo route -n
```and looking next to 0.0.0.0 under Gateway.

And what if you type

```
ping 8.8.4.4
```anything?

Yes I get connected to the router, but i dont get an actual internet connection.. anyway heres the outputs

```

64 bytes from 192.168.2.1: icmp_req=1 ttl=64 time=0.471 ms
64 bytes from 192.168.2.1: icmp_req=2 ttl=64 time=0.496 ms
64 bytes from 192.168.2.1: icmp_req=3 ttl=64 time=0.463 ms

```
 and so on...

when i type ping 8.8.4.4
```

64 bytes from 8.8.4.4: icmp_req=1 ttl=54 time=42.4 ms
64 bytes from 8.8.4.4: icmp_req=2 ttl=54 time=38.6 ms
64 bytes from 8.8.4.4: icmp_req=3 ttl=54 time=39.3 ms


```

---

### Post by Dylan1473 on 2012-08-03
You are in fact connected to the internet then, your DNS settings or server are probably the problem. Open your web browser and try typing in [http://74.125.224.72/](http://74.125.224.72/)

What do you get?

EDIT: Also, right click your network manager icon and select "Connection Information". What does it say next to Primary DNS and Secondary DNS?

---

### Post by Lithum on 2012-08-03
i got google, but when i unplugged my ethernet cable i just got about:blank

---

### Post by Dylan1473 on 2012-08-03
You didn't have your ethernet cable plugged in when you did the pings did you?

EDIT: Also, right click your network manager icon and select "Connection  Information". What does it say next to Primary DNS and Secondary DNS?

---

### Post by Lithum on 2012-08-03
heres the some additional information Im also including from the wireless network tab::


Interface: 802.11 WiFi (wlan0)
Driver: iwlwifi
Speed: 1 Mb/s   (should be 100 Mb/s)

and under the IPv4

Default Route: 192.168.2.1
Primary DNS: 192.168.2.1

IPv6

blank

---

### Post by Lithum on 2012-08-03
ill redo the pings again...


```

PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
kyle@kyle-300V3A-300V4A-300V5A-200A4B-200A5B:~$ ping 8.8.4.4
PING 8.8.4.4 (8.8.4.4) 56(84) bytes of data.

```

---

### Post by Dylan1473 on 2012-08-03
Okay, that DNS should be right I think. Are any other computers on that router successfully using the internet? 

Also, 1Mb/s is really low. And where are you getting 100 from? Your adapter should theoretically support either 150 or 300 I'd think, and your router must be one of 11, 54 or 300. How far away are you from the router? And do you know what type of router you have or any general info about it, by any chance?

EDIT: Okay, those other ones must have been with the ethernet cable connected then? Now you do not have internet. Your connection to your router is also extremely poor if I'm interpreting this correctly. Actually, those last pings didn't seem to reach the router at all.

---

### Post by Lithum on 2012-08-03
Well thats just the funny thing, its fine when im on windows 7 and i have my android and my ps3 using the router without any issues at all, its seems to be an ubuntu specific problem :confused:

I got 100 mb/s from the wired connection tab

even though that in itself is wierd cause i can download music,movies,etc upto speeds of 1.7 mb/sec
Im also approximately..maybe 4,5 feet away from my router.
My router is also a Belkin

---

### Post by Dylan1473 on 2012-08-03
The connection is the actual strength of the signal to your router. Wired signal strength goes in speeds of 10, 100, and 1000 megabits per second (most commonly 100). You won't actually get those full download speeds from wired, but more of it is dedicated to your downloads than wireless.

With wireless, you get speeds of 11 (with wireless b) 54 (with wireless g) and 150 or 300 (with wireless N). I believe a new standard was recently released that allows up to 1300 on one band with wireless, actually. However, I think you lose about half immediately to encryption with wireless, plus more depending on how far you are from the access point, plus there are other factors, so wired is generally better (unless you're using an old 10 megabit wire when you have a newer 300Mb/s router I guess).

What you're seeing is the speed of your connection to the router. It should be listed as either 150 or 300 under ideal circumstances with an N router based on how good a router/wireless adapter you have. It may be 54 or 11 depending on just how old your router is, but if it's either of those (especially 11) you should probably upgrade if you plan to use wireless, the difference will be very noticeable. Also note that there's a difference between megaBITS and megaBYTES. One megabit is about an eighth of a megabyte.

The speeds your getting for downloads of up to 1.7 per second are actually 1.7 megaBYTES for second, which is actually fairly  typical and decent. It's likely that your network infrastructure would support a few times that speed, I know I've managed up to 10MB/s with intranetwork transfers on mine compared to 1.8MB/s tops for internet downloads.

Anyway, sorry for the long lecture, the point is you should have a speed of 150 or 300 or close. 1 is bad. Very bad. It sounds as though the issue isn't that you don't have an internet connection necessarily (though it may be that as well), especially if those earlier pings were over your wireless. It's just that for some reason your wireless signal is so low as to render it useless most of the time.

Can you open a terminal and type iwconfig then post what the output looks like?

EDIT: Sorry that should be sudo iwconfig

---

### Post by Lithum on 2012-08-03
```

kyle@kyle-300V3A-300V4A-300V5A-200A4B-200A5B:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Home Net"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 94:44:52:50:51:06   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:617   Missed beacon:0

eth0      no wireless extensions.

```

---

### Post by Dylan1473 on 2012-08-03
Well, you have an excellent signal. Your transfer speed should be at least 11Mb/s even if you have a very low quality router, and most likely it'd be around 150 to 300. I found _[this thread]("http://ubuntuforums.org/showthread.php?t=1941331")_ where someone is having issues with a similar wireless device - is it helpful at all?

---

### Post by Lithum on 2012-08-03
it wont even let me put the file into the folder, says i dont have the permission to despite the fact i am already administrator

unless if theres a way make the file and insert it with the terminal

---

### Post by Dylan1473 on 2012-08-03
Oh right. Here's the deal: on Ubuntu, for security/safety reasons you don't have full administrative powers. Some Linux variants you can log in as root and you do, but this is for advanced users. Anyway, the way it works is you can do administrative stuff through the sudo command. 

You can move files in the terminal by typing:

```
sudo mv [file/directory] [target directory]
```Where the object might be, say, /home/Lithum/file and the destination might be /home/Lithum/Documents.

You can create new text files by typing

```
gksudo gedit [target directory]/[file name]
```and then saving them. That'll also work to edit existing files. I think you can also place files in the terminal by dragging them in if you don't feel like typing out the entire directory. Be very careful - there's a reason this stuff is restricted.

---

### Post by Lithum on 2012-08-03
ok i tried doing that and i think its trying to 'stat' the file instead of moving the file? :confused:

i slightly recall having a similar problem with 11.04 on my acer laptop as well, but damned if i remember how it was solved

---

### Post by Dylan1473 on 2012-08-03
I don't think I can really offer you that much more help, sorry. It sounds like the problem is with your wireless drivers, if I were to take a guess, and I don't know much about that. My computer came with an atheros based card that worked out of the box and even supports master mode. I bought another adapter for other purposes, but it was also very well supported in Linux. Hopefully someone that knows more about Intel cards than me will happen along and help.

---

### Post by Lithum on 2012-08-03
yeah i hope so, well I appreciate your time and effort, at least we got it narrowed down to what the possibilities can be and i will continue to search out solutions in the mean time.

---

