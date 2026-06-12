---
title: "AP point disassociates, times out"
date: 2010-06-11
forum: General Help
---

### Post by Bucky Ball on 2010-06-11
Hi all,

Wireless is fine while you're using it, leave it for five or ten minutes, come back and dead. Need to restart networking. Persistent prob and have been trying to fix this forever (a few months now). 

iwconfig =

```
wlan0     IEEE 802.11abg  ESSID:"Slynn"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:11:84:AF:26   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality=80/100  Signal level:-54 dBm  Noise level=-83 dBm
          **Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0**
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

The line I have put in bold is strange. Figuring that could have something to do with it?

dmesg =

```
[ 1344.484839] wlan0: AP denied association (code=17)
[ 1344.526464] wlan0: association with AP 00:1b:11:84:af:26 timed out
```

Next time it times out, I will post the whole dmesg before I restart networking.

Any help, the problem is boring and long in the tooth. Apart from that, this Compaq 610 is purring. ;)

---

### Post by Bucky Ball on 2010-06-12
Agh!!!!!! HELP PLEASE! Anyone!

Switch the laptop on today and no wireless but also no network manager. I click it and put in password, get the GUI but it is grey and blank and crashed. Can't click it off or do anything else with it. Have to force quit. Try and open Synaptic Package Manager and tries but GUI won't open.

What is happening??? I really didn't screw with much, just changed a few things on the router and all was working as normal (with network drop outs) before I went to bed, even after a few restarts to make sure. Switching it off overnight probably made all the difference! Damn!

I am desperate and appreciate any ideas people might have. Running from the ethernet cable at the moment. I'm sick of trying to fix quirky things on my wife's lappy when I have end of semester assigniments to complete! Always picks that time to go whacky.

There was a kernel update. Might try from the previous kernel and see if that makes any difference. Hardware?

---

### Post by chayzer on 2010-06-12
lspci?

---

### Post by Bucky Ball on 2010-06-12
Card not the issue. With a lot of screwing around I have gotten it back to where it was. I am yet to see if it is still dropping out but I seem to have fixed a few odd things in the process of trying to get the wireless happening again. 

Long story but the router had defaulted to the factory settings, that included setting its IP back to ending in 1. I had it ending in 2 and the other router ending in 1 so until I unplugged everything from the wireless router and plugged the lappy straight in and figured it was 1 I had no hope; that would have gotten me to the other router if you follow.

Once into the config, I just set up my network again. All the details in network manager were blank or wrong as I had reinstalled and screwed with that so set that up again and all is working for now. I will go away and leave it now for twenty minutes. If the wireless is still up when I try again, problem solved. If not, back to where I started four hours later.

FYI:

```
Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

---

### Post by Bucky Ball on 2010-06-12
Nope, still dropping out. And this is the dmesg directly after it does:

```
[  288.592859] wlan0: RX disassociation from 00:1b:11:84:af:26 (reason=4)
[  288.592868] wlan0: disassociated
[  288.651960] wlan0: associate with AP 00:1b:11:84:af:26
[  288.654103] wlan0: RX ReassocResp from 00:1b:11:84:af:26 (capab=0x431 status=17 aid=1)
[  288.654111] wlan0: AP denied association (code=17)
[  288.661547] wlan0: associate with AP 00:1b:11:84:af:26
[  288.662172] wlan0: RX AssocResp from 00:1b:11:84:af:26 (capab=0x431 status=17 aid=1548)
[  288.662179] wlan0: AP denied association (code=17)
[  288.686638] wlan0: associate with AP 00:1b:11:84:af:26
[  288.688724] wlan0: RX AssocResp from 00:1b:11:84:af:26 (capab=0x431 status=17 aid=1548)
[  288.688731] wlan0: AP denied association (code=17)
[  288.696179] wlan0: association with AP 00:1b:11:84:af:26 timed out
```

Wonder why the AP first dissassociates and then denies association? Any ideas anybody? It really shouldn't be this hard, especially with a release over two years old. But it is ... ;(

---

### Post by Bucky Ball on 2010-06-12
Not throwing the party just yet or marking the thread as solved, I'll give it 48 hours, but this is what I did and it seems to be working. Wireless had been solid for about three hours when we switched it off.

Install wicd, it removes network manager, configure it, and voila; no more probs. For now! Always know if you're seeing the AP because the icon tells you, really easy to configure ... 

If anyone out there is having network randomly drop out, perhaps try wicd, perhaps madwifi for atheros, if you are currently using the default Network Manager. ;) I've tried to fix this problem for ages on and off and there seems to be no clear fix I could find online, plenty with the problem. Is it as simple as Network Manager sucks for some machines in some situations? I've never had problems with it before.

---

### Post by Bucky Ball on 2010-06-13
Just about ready to confirm that wicd has fixed the network random dropout problem. Been on for about three hours so far today, idle periods when off making cups of tea, etc, and hasn't dropped off once. I'm almost ready to try some power saving options again as I switched them all off in case it had something to do with that. I suspect not. 

In twenty four hours I will consider this solved ... ;)

Solved! Wicd seems to have done the trick and hasn't dropped the wireless once. Hurrah! I can't believe the time I have spent on that problem and it was that simple. Oh, well. Live and learn. I am going to post this solution somewhere more obvious than at the end of a dead thread in the hopes I might save others hours of frustration.

---

