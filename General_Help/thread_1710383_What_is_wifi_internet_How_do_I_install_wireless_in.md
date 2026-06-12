---
title: "What is wifi internet? How do I install wireless internet?"
date: 2011-03-19
forum: General Help
---

### Post by brawnypandora0 on 2011-03-19
I'm completely new to computers (less than one year) and Ubuntu (less than a month). When I got wired Internet a few months ago there was this device with a little black antenna on it labeled Netgear Wireless Router MR814v2. Is this thing supposed to be used for wireless Internet? How do I install wireless onto my laptop? Does this mean I'll be able to leave my room with my laptop and then still have Internet without bringing the cord all the time?

---

### Post by brawnypandora0 on 2011-03-19
I'm completely  new to computers (less than one year) and Ubuntu (less than a month).  When I got wired Internet a few months ago there was this device with a  little black antenna on it labeled Netgear Wireless Router MR814v2. Is  this thing supposed to be used for wireless Internet? How do I install  wireless onto my laptop? Does this mean I'll be able to leave my room  with my laptop and then still have Internet without bringing the cord  all the time?

---

### Post by mikewhatever on 2011-03-19
Here is a good explanation->[http://www.howstuffworks.com/wireless-network.htm](http://www.howstuffworks.com/wireless-network.htm)

---

### Post by brawnypandora0 on 2011-03-19
So what are all the steps that I have to make to install this? Printed on the bottom of my laptop is something called "BCM94318MPG" I asked a friend what this meant and he said it's a wireless adapter transmitter module. But he said that Ubuntu doesn't recognize Broadcom wireless adapter transmitter modules. Does this mean I won't be able to have wireless Internet? What are the steps I can take to install it manually?

---

### Post by mikewhatever on 2011-03-19
I don't know if that particular wireless card/module is recognized, I have a BCM4312 which works fine in Ubuntu.

---

### Post by brawnypandora0 on 2011-03-19
Well how do I find out? What are the installation steps? I'm new to computers, not just Ubuntu, so I'm not familiar with most of the terminology.

---

### Post by overdrank on 2011-03-19
Hi and please do not create multiple threads on the same issue. Threads merged :)

---

### Post by thunderbirdje on 2011-03-19
How old is your laptop?

What Ubuntu version do you have? -> With the newer releases (I have 10.10) in combination with a recent (for example mine is 2,5 year) laptop it is very easy to connect to the wireless network.

1. Click the wifi icon in the upper bar (on the right side) and then select the name of your wireless network

2. If your wireless is protected you should probably select the protection (which is most likely WPA or WPA1 personal) and then enter the correct password.

3. If you don't see your wireless network listed, the router is not transmitting the wireless (and yes, you can walk quite far, depending on your router en the walls between you and the router it can be 5 up to 100-200 meters in OPEN field :-))

Have fun and enjoy Ubuntu!

---

### Post by brawnypandora0 on 2011-03-19
My laptop is six years old. I don't know what version of Ubuntu I have. How do I find out? I don't know cause the laptop was given to me as a gift--it was probably installed in 2009 I'm guessing.

1. My wireless name doesn't appear on the list.

2. I don't know whether my wireless is protected. What's WPA? I didn't set up any passwords!?!

3. You're right, it's not listed. Does this mean I have to install it or something? What are the steps?

---

### Post by mikewhatever on 2011-03-19
Can you post the output of the following command from Applications->Accessories->Terminal:
```
lspci -nn | grep -i net
```

In the best case, your card is supported and all there is to do is install a driver from the Ubuntu repositories, in the worst case ... let's not consider this now.:p

---

### Post by brawnypandora0 on 2011-03-19
________________________________________
/ "Be very careful with what you do with \
| IP-tables - it's extremely hard to get |
| right - I've tried to set rules in a   |
| router with IP-tables - small wonder   |
| the thing did not fly out of the       |
| window"                                |
|                                        |
\ Jul 7 2007                             /
 ----------------------------------------
   \
    \
        .--.
       |o_o |
       |:_/ |
      //   \ \
     (|     | )
    /'\_   _/`\
    \___)=(___/

user@user-laptop ~ $ lspci -nn | grep -i net
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 91)
00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
user@user-laptop ~ $

---

### Post by brawnypandora0 on 2011-03-19
So what does all this mean? Will I be able to use wireless internet?

---

### Post by mikewhatever on 2011-03-19
Your wireless card is supposed to work with the b43 driver.
Open Synaptic Package Manager under System->Administration, search for and install the **b43-fwcutter** package. Reboot, and then post the output of the **ifconfig** command.
To find out the version you have, post the output of the **lsb_release -a** command.

---

### Post by brawnypandora0 on 2011-03-19
eth0      Link encap:Ethernet  HWaddr 00:16:36:39:d5:1b  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe39:d51b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:3337 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2684833 (2.6 MB)  TX bytes:404528 (404.5 KB)
          Interrupt:19 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

So what do I do to install wireless. What are the steps?

---

### Post by mikewhatever on 2011-03-19
The wireless card should be working now. Can you post the outputs of the following:

```
lsmod | grep b43

dpkg -l | grep b43-fwcutter
```

PS: ...and here are the steps. Happy now?
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by brawnypandora0 on 2011-03-19
Why is it important to know what version of Ubuntu I have?

---

### Post by brawnypandora0 on 2011-03-19
> **mikewhatever said:**
> The wireless card should be working now. Can you post the outputs of the following:

```
lsmod | grep b43

dpkg -l | grep b43-fwcutter
```PS: ...and here are thhe steps.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

user@user-laptop ~ $ lsmod | grep b43
b43                   157218  0 
mac80211              204922  1 b43
cfg80211              126485  2 b43,mac80211
led_class               2864  1 b43
ssb                    37336  1 b43
user@user-laptop ~ $ dpkg -l | grep b43-fwcutter
ii  b43-fwcutter                          1:012-1build1                                   Utility for extracting Broadcom 43xx firmwar
user@user-laptop ~ $ 

So I can use wireless now? How come my network name still doesn't show up on the list?

---

### Post by bkratz on 2011-03-19
You can see all the available AP's (including yours, I hope)  with a 


sudo iwlist scan

---

### Post by mikewhatever on 2011-03-19
> **brawnypandora0 said:**
> ...

So I can use wireless now? How come my network name still doesn't show up on the list?

Well, knowing the version might help troubleshooting, and I also thought you yourself might want to know. Personally, I couldn't care less. Anyway, another module might be interfering with b43, so please post the output of the **lsmod** command.

---

### Post by brawnypandora0 on 2011-03-19
So why isn't my Netgear Wireless Router MR814v2 showing up? I think my laptop's internal Broadcom BCM94318MPG adapter is fine. Am I supposed to configure the Netgear Wireless Router as well? Or does is it supposed to show up automatically?

Anyway, it's still not showing up on the network list.

---

### Post by brawnypandora0 on 2011-03-19
> **mikewhatever said:**
> Well, knowing the version might help troubleshooting, and I also thought you yourself might want to know. Personally, I couldn't care less. Anyway, another module might be interfering with b43, so please post the output of the **lsmod** command.

Module                  Size  Used by
ipt_MASQUERADE          1407  1 
xt_state                1098  1 
ipt_REJECT              1928  2 
xt_tcpudp               2011  4 
iptable_filter          2271  1 
nf_nat_h323             5077  0 
nf_conntrack_h323      46926  1 nf_nat_h323
nf_nat_pptp             1920  0 
nf_conntrack_pptp       4413  1 nf_nat_pptp
nf_conntrack_proto_gre     4021  1 nf_conntrack_pptp
nf_nat_proto_gre        1259  1 nf_nat_pptp
nf_nat_tftp              716  0 
nf_conntrack_tftp       2893  1 nf_nat_tftp
nf_nat_sip              5108  0 
nf_conntrack_sip       15389  1 nf_nat_sip
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
nf_conntrack_ftp        5381  1 nf_nat_ftp
iptable_nat             4414  1 
nf_nat                 15735  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      10672  4 iptable_nat,nf_nat
nf_conntrack           61583  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
ip_tables               9991  2 iptable_filter,iptable_nat
x_tables               14299  6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables
binfmt_misc             6587  1 
ppdev                   5259  0 
dm_crypt               11331  0 
snd_intel8x0           25588  3 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
joydev                  8708  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
arc4                    1153  2 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 33024  0 
snd                    54148  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
soundcore               6620  1 snd
b43                   157218  0 
i2c_sis96x              3024  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
mac80211              204922  1 b43
shpchp                 28820  0 
k8temp                  3024  0 
lp                      7028  0 
serio_raw               3978  0 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
cfg80211              126485  2 b43,mac80211
parport                32635  2 ppdev,lp
led_class               2864  1 b43
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
sis_agp                 4047  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
amd64_agp               7025  1 
usbhid                 36110  0 
ssb                    37336  1 b43
sis900                 17048  0 
mii                     4381  1 sis900
vga16fb                11385  1 
vgastate                8961  1 vga16fb
agpgart                31724  2 sis_agp,amd64_agp
hid                    67032  1 usbhid

---

### Post by bkratz on 2011-03-19
> **brawnypandora0 said:**
> So why isn't my Netgear Wireless Router MR814v2 showing up? I think my laptop's internal Broadcom BCM94318MPG adapter is fine. Am I supposed to configure the Netgear Wireless Router as well? Or does is it supposed to show up automatically?

Anyway, it's still not showing up on the network list.



Calm down, you are just about there!  Do you see other AP's? Other than yours. Are you broadcasting the essid from the router or do you have it hidden?

---

### Post by brawnypandora0 on 2011-03-19
Am I supposed to set up my Netgear wireless router or something? How do I do that?

---

### Post by brawnypandora0 on 2011-03-19
> **bkratz said:**
> Calm down, you are just about there!  Do you see other AP's? Other than yours. Are you broadcasting the essid from the router or do you have it hidden?

What's an AP? What's essid?

---

### Post by mikewhatever on 2011-03-19
I don't see any other wireless modules, could you try and post the output of **ifconfig** again. Obviously, you also have to setup the router.

PS: Are you in a hurry or something? Did you look at the link from post #2?

---

### Post by bkratz on 2011-03-19
> **brawnypandora0 said:**
> What's an AP? What's essid?



Here is a link to your manual regarding the ssid broadcast and how to see if it is enabled.

[http://kb.netgear.com/app/answers/detail/a_id/75/session/L2F2LzEvc2lkL3FSM01vbXBr](http://kb.netgear.com/app/answers/detail/a_id/75/session/L2F2LzEvc2lkL3FSM01vbXBr)

---

### Post by bkratz on 2011-03-19
Here is a link about _A_ccess _P_oints  (APs)

[https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint)

---

### Post by brawnypandora0 on 2011-03-19
> **bkratz said:**
> Here is a link to your manual regarding the ssid broadcast and how to see if it is enabled.

[http://kb.netgear.com/app/answers/detail/a_id/75/session/L2F2LzEvc2lkL3FSM01vbXBr](http://kb.netgear.com/app/answers/detail/a_id/75/session/L2F2LzEvc2lkL3FSM01vbXBr)

That's so weird! I typed in 192.168.0.1 and the setup screen did not have a page that looks like the screenshot page. I don't see the Enable Wireless Router Radio box anywhere.

---

### Post by SuaSwe on 2011-03-19
NETGEARs sometimes have setup wizards that will not give you a menu to the left (you can still get to that page but additional steps are required). What are you seeing once logged onto 192.168.0.1?

---

### Post by bkratz on 2011-03-19
And here is a link to the download of your whole manual--just in case you don't have the original.

[http://kb.netgear.com/app/products/model/a_id/2503](http://kb.netgear.com/app/products/model/a_id/2503)

---

### Post by brawnypandora0 on 2011-03-19
The toolbar on the left looks exactly the same as the screenshot for 
[http://kb.netgear.com/app/answers/detail/a_id/75/session/L2F2LzEvc2lkL3FSM01vbXBr](http://kb.netgear.com/app/answers/detail/a_id/75/session/L2F2LzEvc2lkL3FSM01vbXBr)
but unlike the screenshot there's no page called "Advanced Wireless Settings." I do have "Wireless Settings" under Setup which has [**Wireless Access Point**]("javascript:loadhelp('_wire','broadcast')") 	   	 Enable Wireless Access Point   	      Allow Broadcast of Name (SSID) 
which I've enabled. but I can't find enable wireless router radio anywhere.

---

### Post by brawnypandora0 on 2011-03-19
Man, are all Broadcoms this confusing? I can see my network on the list now, but it's now asking for a key with wireless security WEP 40/128-bit key. I copied and pasted WEP Key 1 under the wireless settings tab (it's an auto-generated one 26 characters long), but it's still not working.

Since I see my network on the list, does this mean my wireless router radio is enable?

---

### Post by abyrne on 2011-03-19
If you see your network's name on the list, then your router is indeed broadcasting. Does your router offer a different security mode, such as WPA? WEP security is outdated, and can be cracked within minutes. WPA uses a simple password of your choosing, and is much more secure.

Oh and your Broadcom adapter is, if I'm understanding the situation correctly, working correctly. It's just your wireless router that requires some extra configuration.

---

### Post by bkratz on 2011-03-19
> **brawnypandora0 said:**
> Man, are all Broadcoms this confusing? I can see my network on the list now, but it's now asking for a key with wireless security WEP 40/128-bit key. I copied and pasted WEP Key 1 under the wireless settings tab (it's an auto-generated one 26 characters long), but it's still not working.

Since I see my network on the list, does this mean my wireless router radio is enable?

I would suspect that your statement "
 Wireless Access Point[COLOR="Red"] Enable Wireless Access Point[/COLOR] Allow Broadcast of Name (SSID) 
which I've enabled."

is an equivalent name to " wireless router radio is enabled"

The next step I would take would be to try other encryption (none--WPA--WPA2) until I found one that I was comfortable with how it worked. Also do not use WPA/WPA2 mixed mode (try them separately)  if that is a choice on the router--often it causes difficulties. WEP is not very secure anyway--only slightly better than none.

---

### Post by brawnypandora0 on 2011-03-19
My router only uses WEP. Whatever, I'll use it. Why isn't it working?

---

### Post by abyrne on 2011-03-19
> **brawnypandora0 said:**
> My router only uses WEP. Whatever, I'll use it. Why isn't it working?

Well there could be a lot of different problems right now. Try temporarily disabling the security on the network, then try to connect.

---

### Post by SuaSwe on 2011-03-19
Having read around a bit, it looks like it might be better to configure WEP in command line instead of using the graphical netwokr management interface.

To do this, first do:

```

ifconfig

```

.. and find the name of the wireless interface (e.g. wlan0), then do:

```

sudo iwconfig wlan0 essid <insert network name here>
sudo iwconfig wlan0 key <insert WEP here>
sudo ifconfig wlan0 up

```

... substituting "wlan0" with whatever your WLAN interface is called. :) Remember that both network name and key need to be written exactly as they are on the router. I would also recommend using a netork name made up of only one word, without special characters. 

I'm not sure if some more steps are involved there as I've never had to do this, but I'm sure someone could advise if so. :)

---

### Post by brawnypandora0 on 2011-03-20
How do I know what my wireless interface name is? What does all that do?

Also, should my authentication type be set to Open System, Automatic, or Shared Key?

Also, why are there four Security Encryption Keys (WEP) under "Wireless Settings"? I've typed in all four of them and my wireless still isn't working.

Could it be that my Netgear doesn't recognize Linux? My model was made in 2003.

---

