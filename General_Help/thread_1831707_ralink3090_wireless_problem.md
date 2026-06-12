---
title: "ralink3090 wireless problem"
date: 2011-08-23
forum: General Help
---

### Post by loolooyyyy on 2011-08-23
**ALL SOLVED, read the next two posts**

i know there is thousand of articles on this but DO NOT refer me to those, since none of them worked

the problem is the very low quality of wifi (works only in 2meter range)

i have ra3090 hardware
```
uname -a:
Linux king 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```I've compiled and installed the official driver from ralink with wpa2 support, installed it, blacklisted rt2800sta
now 2860 loads signal quality was 33/70 (with rt2800)
now it's 99/100 but keep showing the password dialog after each attempt to connect (means it doesn't connect)
password is WPA2, and can not be changed to WEP or something

---

### Post by loolooyyyy on 2011-08-23
did some crazy stuff from here:
[http://ubuntuforums.org/showthread.php?t=1476007&highlight=RT3090](http://ubuntuforums.org/showthread.php?t=1476007&highlight=RT3090)
now it says rt2860sta, signal quality 10/100, and doesn't connect

---

### Post by loolooyyyy on 2011-08-23
ok fixed it, since the solution was for another card and not 3090, and there are LOT of people having trouble, i write it for 3090:

**1.download official ralink driver for 3090**
[http://t3s.ralinktech.com.tw/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09URTJORFF5TWpreU9TNTZhWEE5UFQweU1ERXdYekV5TVRkZlVsUXpNRGt3WDB4cGJuVjRVMVJCWDFZeUxqUXVNQzQwWDFkcFJtbENWRU52YldKdlgwUlFUdz09Qw%3D%3D]("http://t3s.ralinktech.com.tw/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09URTJORFF5TWpreU9TNTZhWEE5UFQweU1ERXdYekV5TVRkZlVsUXpNRGt3WDB4cGJuVjRVMVJCWDFZeUxqUXVNQzQwWDFkcFJtbENWRU52YldKdlgwUlFUdz09Qw%3D%3D")

**2.unzip it**
*i assume the folder name is 2010,if it isn't, rename it to make things easier *
[B]
3.locate the file ./2010/os/linux/*config.mk* [/B]for editing**, **nano,gedit whatever you are comfortable with!

**4.locate**   **HAS_WPA_SUPPLICANT** and check the option to be **"y"** like **HAS_WPA_SUPPLICANT=y**

**5.locate**   **HAS_NATIVE_WPA_SUPPLICANT_SUPPORT** and make sure it says "y" **HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y**

**6.locate**   **HAS_CFG80211_SUPPORT** change to** "n"** or you will face an error later,so it will be **HAS_CFG80211_SUPPORT=n**
[B]
7.locate[/B] the file** ./2010bkup/common/cmm_wpa.c**, change **WPA_MIX_PAIR_CIPHER        FlexibleCipher = MIX_CIPHER_NOTUSE;**  to  **WPA_MIX_PAIR_CIPHER FlexibleCipher = WPA_TKIPAES_WPA2_TKIPAES;**  with the semicolon at the end 
**ATTENTION**: this is a "c" language file, pay attention to the part after **"//"** so it doesnt go to a new line, it stays after** "//"**, you can simply remove it, it says " *//it provide the more flexible cipher combination in WPA-WPA2 and TKIPAES mode*" and it's a lie :D ,also dont forget ***"*;*" ***at the end of line BEFORE[B] "//"
Attention2: [/B]if you open the file with gedit it gives an error about encoding, from the pulldown menu choose western

*make sure you have gcc installed*, 
**8.from terminal go to directory 2010** and issue these command **ALL AS ROOT**, even make: 
```


[LIST]
[*]sudo make
[*]sudo make install
[*]sudo ifconfig wlan0 down
[*]sudo rmmod rt3090sta
[/LIST]

[LIST]
[*][FONT=Verdana, sans-serif]sudo mv /lib/modules/2.6.38-11-generic/kernel/drivers/staging/rt2860/rt2860sta.ko ~/rt2860sta.ko     ==>[I]NOT so sure about this one, but i did it, and also change the number 2.6.38.11 to your current kernel
[/I][/FONT]
[*][FONT=Verdana, sans-serif]sudo depmod -a[/FONT]
[*][FONT=Verdana, sans-serif]sudo modprobe rt3080sta[/FONT]
[/LIST]

```[B]NOW THE WIRELESS WORKS BUT...
[/B]if you restart, you need two do the last two (three?) commands from the box above again, the solution is doing these steps [B]BUT I DID IT AND IT DIDN'T WORK
[/B]```

[LIST]
[*]cd ./2010/os/linux/
[*]sudo cp rt3090sta /lib/modules/2.6.38-11-generic/kernel/drivers/staging/rt2860/
[*]or if the file doesnt exist "sudo cp rt2860sta /lib/modules/2.6.38-11-generic/kernel/drivers/staging/rt2860/"
[/LIST]

```[B]
9.[/B] at the end of the file** /etc/modules** add **"rt3090sta**" without quotations.
**10**.restart and hope it works 
**10.5 **from now on you might have to access your card by the name "ra0" instead of "wlan0"

ps: i **DIDN'T** blacklist any driver by modifying /etc/modprobe.d/blacklist.conf

thanks to [Sven6210]("http://ubuntuforums.org/member.php?u=929104") (A LOT!!!) for the original idea who her/himself thanked [FONT=Verdana, sans-serif]Chris Baker
and the one who told me to do these stuff for 3090 instead of 2860
and all those who actually help me here at forum, really appreciate their work
my english is not so good,but i did my best

[/FONT]

---

### Post by nucleon on 2011-10-15
Thanks, appears to work for my rt3090 in acer aspire z6510. 
In lsmod the rt3090sta module appears, but in iwconfig it comes up as ra0 (as you said) with: Ralink STA  ESSID  Nickname:"RT2860STA". Because the rt3090 driver is based on the 2860sta driver? 
Oh well, seems to be working better than my other makeshift resolution for the wireless, deblacklisting rt2800pci.

---

### Post by loolooyyyy on 2011-10-16
yes that's right
if you dig through the rt3090's driver source code, you see it's called 2860

---

