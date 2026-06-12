---
title: "Wireless is disabled"
date: 2011-04-23
forum: General Help
---

### Post by ChaosChris2009 on 2011-04-23
Hello, I am testing Ubuntu 11.04 Beta 2 (32-Bit) on a Compaq Preasrio CQ60 215DX notebook laptop.

The wireless was working just fine this morning, but now it's telling me that wireless is disabled.

I'm posting from another laptop which is running W7 Ultimate.

---

### Post by PhillyPhil on 2011-04-23
You bumped the wifi switch on the side of the laptop to off? :p

---

### Post by josephmills on 2011-04-23
could you please press ctrl+alt+t then enter in ```
rfkill list all
``` then post that here thanks

---

### Post by ChaosChris2009 on 2011-04-23
> **josephmills said:**
> could you please press ctrl+alt+t then enter in ```
rfkill list all
``` then post that here thanks

```

		0: hp-wifi: Wireless LAN

	Soft blocked: yes

	Hard blocked: no

1: phy0: Wireless LAN

	Soft blocked: yes

	Hard blocked: no

```

---

### Post by josephmills on 2011-04-23
now try ```
rfkill unblock all
``` but dont reboot tell us what happens

---

### Post by ChaosChris2009 on 2011-04-23
Same result, nothing happens. Enable Wireless is now greyed out and I can't enable if I want. Terminal gives back nothing. And now it's saying wireless is disabled by hardware switch

---

### Post by josephmills on 2011-04-23
> **ChaosChris2009 said:**
> Same result, nothing happens. Enable Wireless is now greyed out and I can't enable if I want. Terminal gives back nothing. And now it's saying wireless is disabled by hardware switch

is ```
rfkill list all
``` still the same?

---

### Post by ChaosChris2009 on 2011-04-23
> **josephmills said:**
> is ```
rfkill list all
``` still the same?

Different this time

```
0: hp-wifi: Wireless LAN

	Soft blocked: yes

	Hard blocked: yes

1: phy0: Wireless LAN

	Soft blocked: no

	Hard blocked: no

```

---

### Post by josephmills on 2011-04-23
ok now press the button next to the power button rfkill shows if the switch is off that is the hard the soft is for software so press the button and then try ```
rfkill list all
``` you want to see no everywhere after you get the hard block off then ```
rfkill unblock all 
```should do the rest but if not we will  start to dig

---

### Post by ChaosChris2009 on 2011-04-23
> **josephmills said:**
> ok now press the button next to the power button rfkill shows if the switch is off that is the hard the soft is for software so press the button and then try ```
rfkill list all
``` you want to see no everywhere after you get the hard block off then ```
rfkill unblock all 
```should do the rest but if not we will  start to dig

This happens


```
chrisv@chris:~$ rfkill list all

1: phy0: Wireless LAN

	Soft blocked: no

	Hard blocked: yes

chrisv@chris:~$ rfkill unblock all

chrisv@chris:~$ rfkill list all

1: phy0: Wireless LAN

	Soft blocked: no

	Hard blocked: yes

chrisv@chris:~$ 

```

When I try ```
sudo rmmod -f hp-wmi
``` I have the option to join hidden networks or to create networks.

I can't view any networks though, and if I attempt any rfkill commands it goes back to being blocked and wireless disabled.

---

### Post by josephmills on 2011-04-23
> **ChaosChris2009 said:**
> This happens


```
chrisv@chris:~$ rfkill list all

1: phy0: Wireless LAN

	Soft blocked: no

	Hard blocked: yes

chrisv@chris:~$ rfkill unblock all

chrisv@chris:~$ rfkill list all

1: phy0: Wireless LAN

	Soft blocked: no

	Hard blocked: yes

chrisv@chris:~$ 

```

When I try ```
sudo rmmod -f hp-wmi
``` I have the option to join hidden networks or to create networks.

I can't view any networks though, and if I attempt any rfkill commands it goes back to being blocked and wireless disabled.
a hard block means that the physical switch is turned off and needs to be turned on but lets take a look at ```
dmesg | grep ath5k
``` thanks

---

### Post by ChaosChris2009 on 2011-04-23
I have no idea what I did, but I ran rfkill ublock wifi and now I'm back online

Thanks for your help though.

---

### Post by unadulterated on 2011-04-28
I am having issues with Natty 11.04 just installed.. and it shows "wireless is disabled by hardware switch"

my wirelss used to work fine with 10.10 but this is something new.. and only hardware switch I have is ON.

rfkill list all:

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

i tried rfkill unblock all
but the hardware blocked remained.

after restarting twice.. I was able to get the hard blocked : no..
and now its working.. the wifi.

please do these things.. I dont know why but after 2 restarts.. it worked.. and this should be informed to developers, please rectify this.

---

### Post by mlepage on 2011-04-28
This may be related... I was installing 11.04 (final) this morning and couldn't get on wireless, I had to use an eth0 cable. I'd been on the same wireless before. And now I'm reinstalling (from scratch) and this time I could get on the wireless. So maybe something is flaky.

When I couldn't get on, I would click on the wireless entry, but nothing would happen. I also tried turning wireless off and on, no result. I did check my hardware switch was on.

---

### Post by abhinavsood on 2011-04-30
I upgraded to Ubuntu 11.04 on my Compaq Presario v6409 laptop and faced the same problem. Here's how I sorted it out though.

[Make sure you've enabled wi-fi from the hardware switch]

1. Go to System > Administration > Hardware/Additional Drivers and uninstall the STA driver. Don't close the window yet.

2. Open terminal and type ```
rfkill unblock all
```

3. Activate the STA driver again.

That worked for me. :guitar:

---

### Post by Hal1ow3en on 2011-05-15
My girlfriends netbook suddenly stopped working 

1: phy0: Wireless LAN

    Soft blocked: no

    Hard blocked: yes

seem to get the above message when using the rfkill list all command no idea how to get the wireless back on nothing I've read so far has helped. It looks like the people who get wireless back are just lucky any help would be appreciated.

---

### Post by Mhable on 2011-05-17
Okay I have a Compaq CQ60 615dx. I am running Ubuntu 11.04. I was experiencing the same problem and have finally fixed it. 

My steps for fixing the problem were as follows.

1 Open the terminal and enter "rfkill list all"

2 View the output. you want all nos

3 If it says hard blocked yes press the Fn and wifi button at the same time.

4 Next enter "rfkill unblock all" and "rfkill unblock wifi"
      (at this point the wifi button should be blue)

5 Enter "rfkill list all" again just to make sure everything says     no then.

6 Lastly go to the wifi area on the top bar and select enable wireless internet then your wifi network.

Hope this helps someone resolve the problems they are facing getting their wifi working.

---

### Post by bvrabete on 2011-08-06
I have a similar problem: Wireless is disabled and none of the suggestions above seem to work.

When running: 

rfkill list all

I get:

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

Running 

rfkill unblock all or rfkill unblock wifi

makes no difference: acer-wireless remains soft blocked.

Here's the some interesting output from dmesg:

[ 9864.314050] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9899.661087] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10085.010386] r8169 0000:03:00.0: eth0: link up
[10267.087863] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Any hints?

The machine is a Lenovo B570 and I'm running Ubuntu 11.04 (32 bit). 

Brad

---

### Post by gandaran on 2011-08-06
> **bvrabete said:**
> I have a similar problem: Wireless is disabled and none of the suggestions above seem to work.

When running: 

rfkill list all

I get:

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

Running 

rfkill unblock all or rfkill unblock wifi

makes no difference: acer-wireless remains soft blocked.

Here's the some interesting output from dmesg:

[ 9864.314050] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9899.661087] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10085.010386] r8169 0000:03:00.0: eth0: link up
[10267.087863] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Any hints?

The machine is a Lenovo B570 and I'm running Ubuntu 11.04 (32 bit). 

Brad
yes, do you need to install wireless drivers first? what brand of wireless chipset?

---

### Post by bvrabete on 2011-08-07
> **gandaran said:**
> yes, do you need to install wireless drivers first? what brand of wireless chipset?

Wireless chipset is Atheros:
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

The driver is installed: 
lsmod |grep ath
ath9k                 103669  0 
mac80211              257001  1 ath9k
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
cfg80211              156212  3 ath9k,mac80211,ath

---

### Post by wildmanne39 on 2011-08-07
Hi, try this command.
```
rmmod -f acer-wmi
```
unplug you wire connection first then run the command and do not restart your computer, if it works we will need to make it persistent.
Thank you

---

### Post by bvrabete on 2011-08-10
> **wildmanne39 said:**
> Hi, try this command.
```
rmmod -f acer-wmi
```unplug you wire connection first then run the command and do not restart your computer, if it works we will need to make it persistent.
Thank you

Yes, it worked (after a bit of fiddling). I had to leave the acer_wmi module loaded, enable wireless by pressing Fn+F5 key combination then unload the acer-wmi module. After removing the module the system automatically connected to my wireless.

How do I make this permanent? Is this about adding acer-wmi to the module blacklist? If so, what is going to handle the key combination? Until now the wireless was disabled by default.

Thanks for your help!

B

---

### Post by wildmanne39 on 2011-08-25
Hi, this is how you make it persistent.
```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```
I am sorry it has taken me so long to get back to you I have been very sick.

---

### Post by bvrabete on 2011-08-26
> **wildmanne39 said:**
> Hi, this is how you make it persistent.
```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```
I am sorry it has taken me so long to get back to you I have been very sick.

I should have said I had that figured out. It works fine. It would have been better to have it running without having to disable to special keys (like volume etc) but it is better than not having wireless.

Thanks!

---

### Post by wildmanne39 on 2011-08-26
Hi, your welcome! I am glad it is working.

---

