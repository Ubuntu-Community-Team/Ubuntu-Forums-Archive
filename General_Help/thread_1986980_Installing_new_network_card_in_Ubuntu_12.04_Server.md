---
title: "Installing new network card in Ubuntu 12.04 Server"
date: 2012-05-25
forum: General Help
---

### Post by failmaster on 2012-05-25
Hello all, I am trying to install or make work a new network card I installed on my server. Basically changed the card out since the old on was a 10mb/s and the new one is 100mb/s. Yes running fairly old hardware here lol.
The card itself is seated correctly, lights up, and detects cable connection.
Anyway, now eth0 is not present when ifconfig is run. If one runs ```
sudo lshw -C network
``` I do find a network card.
It's a:
```
DECchip 21140 [fasterNet]
local name: eth1
version 22
driver = tulip
driver version = 1.1.15
```

It states that is its disabled. Not sure how to enable it... ```
sudo ifconfig eth1 up
``` does not seem to do the trick.
When doing the ifconfig up, it does then show in ifconfig, but if I try to ping anything on my network, it does not work.
Also ifconfig does not show any IP or anything like that.

Now I have found a thread [here]("http://ubuntuforums.org/showthread.php?t=803436")
that suggests using modprobe, but even after looking at the manual for it, I do not know what to enter to use it with my card.

I have edited ```
/etc/network/interfaces
``` to give eth1 dhcp, but if it can be possible, it would be nice to have this card on eth0, as that has already been configured for thing such as file server, etc.

Please let me know if there is more info that I need to post, or any clarifications.

Thanks!

---

### Post by chili555 on 2012-05-25
Let's see:```
cat /etc/network/interfaces
dmesg | grep -e eth1 -e tulip
```Are you running a desktop environment and Network Manager?

---

### Post by failmaster on 2012-05-25
Sorry for the long wait, was away and then forums locked me out. Not sure what you are looking for there, cuz its a long list to type up :( and since no network no easy way to get it here. Anyway here we go;

```
cat /etc/network/interfaces
(leaving out commented sections)

auto lo
iface lo inet loopback
auto eth0
iface eth1 inet dhcp

```
and here I caught one of my issues, the auto eth0 instead of eth1. Replaced it, restarted it with ```
sudo /etc/init.d/networking restart
``` (also it says that this way of restarting is deprecated, can you tell me a better way to do it plz)

It took a whole lot of time to reconfigure the network interfaces, but it ultimately failed to bring up eth1.

now onto dmesg | grep -e eth1 -e tulip
There is a lot that pertains to media and its speeds, but an interesting point here:
```
tulip 0000:02:0d.0: eth1: tulip_stop>rxtx() failed (CSR5 0xfc660000 CRS6 0x32042202)
```

Anything else?
Thx again!

---

### Post by tlan on 2012-05-25
the new nic should have an entirely different network ID #
when you do a ifconfig in terminal are there several network cards I.E eth1 eth2 or even eth4

check out this post

[http://ubuntuforums.org/showthread.php?t=771981](http://ubuntuforums.org/showthread.php?t=771981)

Tlan

---

### Post by failmaster on 2012-05-25
Hello tlan, the old nic came out and the new nic went in.
If at all possible, it would be great to have it on eth0, but its rly not that big of an issue if it is not.

The issue is that the new nic, eth1, is not active, its DISABLED, when checking as in my post above. trying to restart networking also fails (see my 2nd post).

At first there was only the loopback when I did an ifconfig. After doing ifconfig eth1 up, it showed, but it is not really up, its still broken.

---

### Post by chili555 on 2012-05-25
> tulip_stop>rxtx() failed (CSR5 I think that's a problem and is the root of DISABLED. I've Googled it a bit and haven't yet found a solution. I wonder if the card is defective.> If at all possible, it would be great to have it on eth0, but its rly not that big of an issue if it is not.It's easily done, but let's see if it works correctly first.

I am off to bed, I'll research more tomorrow.

---

### Post by failmaster on 2012-05-26
Hey Chili, thanks a lot for the help. I saw the post from tlan, and I will be editing the file to make it eth0. Maybe that will fix something, I am wondering.

The card is oldish but was working fine the last time I checked and it sat in a box for a few years. Basically when I took it out it looked new, not even dust on it. I did check it visually for defects, but you know that that is not enough.

If there are any software tools to check if the device is operational let me know please.

If there is nothing else that comes to mind, I can stick it in my win7 PC and see if if works there.
Now its a simple PCI card, but I am wondering if there might be any compatibility issues with the mobo...

---

### Post by chili555 on 2012-05-26
> Hey Chili, thanks a lot for the help. I saw the post from tlan, and I will be editing the file to make it eth0. Maybe that will fix something, I am wondering.I highly doubt it, but you are welcome to try. Please do:```
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
```There should be a listing in there for your old NIC, named eth0 and probably *not* using the tulip driver. Remove that whole long line entirely. Be very careful to eliminate only the line you know relates to the old NIC. Now change the line for the new NIC from eth1 to eth0. Proofread carefully, save and close gedit. If you think you've made a mistake, close gedit *without saving* and start over. If in doubt, stop and ask here.

Now you have a thoroughly confused system, so reboot immediately. Is it eth0 now? Is dmesg still as alarming?

You might try switching the card to another PCI slot.

It would be very helpful if you captured your entire dmesg into a text document:```
dmesg > failmaster.txt
```Find the text file in your user directory and transfer it on a USB key or similar and post it here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Post back and give us the link so we can see all the tulip, PCI bus and eth0 activity.

---

### Post by failmaster on 2012-05-26
Ok Chili, will do, I did think about sending it over to a file and getting it to you last time, but was like, sorry its 4am here, not gonna do that now :)

Thanks again for the help btw, I'll do the changes and get you the info needed. Do allow me a few mins (10+).

---

### Post by failmaster on 2012-05-26
[B]There are 2 pages now -> dmesg result is posted on the 2nd page -->>
[/B]

also forgot, this appears after boot:

```
fsck from util-linux 2.20.1
/dev/sda1: clean, 37557/2411920 files, 1862291/9641472 blocks
waiting for network configuration
waiting up to 60 more seconds for network configuration
```

---

### Post by failmaster on 2012-05-26
Got the whole contents of dmesg:

[http://paste.ubuntu.com/1008261/](http://paste.ubuntu.com/1008261/)

---

### Post by chili555 on 2012-05-26
> **failmaster said:**
> Got the whole contents of dmesg:

[http://paste.ubuntu.com/1008261/](http://paste.ubuntu.com/1008261/)It all looks pretty normal until *tulip 0000:02:0d.0: eth0: tulip_stop_rxtx() failed (CSR5 0xfc660000 CSR6 0x32042202)*. I notice you got it to read eth0 painlessly. I have Googled it extensively and found no fix. I suggest you try anothe PCI slot or trouble-shoot the card in, ideally, another Ubuntu machine. It is not only the card that may be old and creaky but also the driver. 

You might also try the live CD for Ubuntu 10.04 and see if it works. 

What is the pci.id? It is an eight-character code like 1317:0985:```
lspci -nn | grep 0200
```

---

### Post by failmaster on 2012-05-26
I will check if the card got dislodged just a tiny bit when skrewing it in. If that does not fix it I will try 10.04. If that also fails, I will try a diff PCI port (old card was in the same this new card is in). If that fails too, I will try to put in the old card, change the settings back and see what happens then.

The ID is 1011:0009


Thx a ton again, lets see what tomorrow brings, its 3:30am here, time for bed lol.

---

### Post by failmaster on 2012-05-27
So I took out the new NIC, and when I did, I noticed that the PCI slot was a tad bigger than the card connector length. About 1mm if that. I took out the old card, and other cards in there, and they all fit the slot perfectly. Potentially this is the cause of the incompatibility.

I stuck the old card back in, booted up, changed /etc/udev/rules.d/70-persistent-net.rules back to use the old card, and now my PC keeps on rebooting after spewing something about finding the old card and being unable to handle some kernel request.

I think I killed it lol. Well this might be the kick I needed to format the thing and see if a clean install with the new card might work. If not I guess I'll go find some other old clunker.

I wanted to thank you very much for all the time and effort you put into helping me!

---

### Post by chili555 on 2012-05-27
> now my PC keeps on rebooting after spewing something about finding the old card and being unable to handle some kernel request.
I am very sorry to hear that. > I stuck the old card back in, booted up, changed /etc/udev/rules.d/70-persistent-net.rules back to use the old card,I think it might have been better to get the old card up and running before changing any /etc files.

Will it boot properly with no NIC card at all? Or have you already started the format and clean install process?

---

### Post by failmaster on 2012-05-27
No worries, not like I did not expect something to go sideways when tinkering.

> **chili555 said:**
> 
Will it boot properly with no NIC card at all? Or have you already started the format and clean install process?

Have not tried, but gonna give it a try as I have not yet formatted.

---

### Post by failmaster on 2012-05-27
Yup, the system is back up and running. I must have messed something up when editing the file ```
/etc/udev/rules.d/70-persistent-net.rules
``` not sure why or how.

The file now has 3 lines, line 1 and 3 being the same (visually checked). Commented out the first line, uncommented the 3rd and changed to eth0.

Booting comp now worked fine, yet networking is still not working.

---

### Post by failmaster on 2012-05-27
woot, after a eth0 down, eth0 up, and restarting networking (again it says its deprecated, and should use the service instead: eg: service smbd reload, does it matter? is there a better way? do let me know plz)

I pinged first my router and then google and it worked fine. I think we are good to go ... on the old card.

Now, I guess its time to mess with things some more, and try and do the same thing with the newer card, if it decides to work...

Question, should I delete the 3 lines in the /etc/udev/rules.d/70-persistent-net.rules that specify old info b4 putting in the new card? Well, lets give it a try anyway haha...

---

### Post by failmaster on 2012-05-27
So, after that little test, I did the same thing, took eth0 down, back up, restarted networking, and I am now able to ping with the "new" card. Pinged google just fine.

I now need to put it on a static IP, which it was on one before. I un-comment the /etc/network/interfaces and then restart networking again. Checked ifconfig, not the correct IP, .16 ending when I want .10

So I restart, now at the start, the machine waits for network config... for a good 2-3 mins. I get back in, and there are issues. In ifconfig RX errors: 1, TX errors: 12 so I bring eth0 down and up again, 2 RX errors now (same TX errors, 12).

I restart networking, this time instead of retarding pretty much immediately, it hangs there. I shut off my modem / router every day, so the .10 IP should be free but will check that as well.

Any Ideas on the new development?

---

### Post by failmaster on 2012-05-27
After a bit more tinkering I was able to find it was a silly error, left dhcp in the file /etc/networking/interfaces but specified IP and all the rest. I changed that to 'static' and everything is working much better now. Am able to ping google, etc.

The issues that I now have are reaching the PC through the network. I have enabled SSH and Transmission with remote GUI connectivity, and both do not seem to be able to reach the server.

Update:
Now the ubuntu pc cannot ping anything, router, other computers on the network, google, etc. I restarted all PCs attache;d to the network, turned off the modem / router, turned it back on, the the ubuntu pc, then the windows one.

Not sure why it is so hit or miss...

---

### Post by chili555 on 2012-05-27
> Update:
Now the ubuntu pc cannot ping anything, router, other computers on the network, google, etc. I restarted all PCs attache;d to the network, turned off the modem / router, turned it back on, the the ubuntu pc, then the windows one.

Not sure why it is so hit or miss...Then you are not really connected. Let's see:```
dmesg | grep eth0
cat /etc/network/interfaces
```Is it the Tulipmobile in the PC now or some other?> woot, after a eth0 down, eth0 up, and restarting networking (again it says its deprecated, and should use the service instead: eg: service smbd reload, does it matter? is there a better way? do let me know plz)If the interface is properly described in /etc/network/interfaces, then all you need to do is:```
sudo ifdown eth0 && sudo ifup eth0
```Verify with:```
ping -c3 192.168.whateverthe.routeris
```

---

### Post by failmaster on 2012-05-27
Yea I have done all that, I know how to ping and, for some reason, when the new card was on DHCP, it worked, i could ping google, but I did not try to see if windows could ping it. I then changed to static IP, and there it all went south. It seems like it did so in stages.

This behaviour feels very much like a defective card. I can always put in the old one and go from there, but since the old one gives 1mb/s xfer rates, it kinda defeats the purpose of a file server, even if it was for home use.

Thanks again for the continued help.

---

### Post by failmaster on 2012-05-29
Well after another few back and forths, I can tell that the issue is for sure with the new card. It is either damaged or incompatible. I am banking on damaged, not sure how it happened, but I got it once to actually work on DHCP for a few minutes, and then it just started not working anymore.

I will stick it in a windows pc one day to check that it was not a compatibility issue, but I am fairly sure it was hardware issues.

Thanks all for the help!

>>Closed<<

---

