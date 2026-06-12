---
title: "Oops, I think I just broke my Ubuntu..... Again :("
date: 2006-04-12
forum: General Help
---

### Post by Goonie on 2006-04-12
Hi guys

I need help... I just can't seem to get things right. I have an Intel 2200BG wireless card in my laptop and it's giving me hell. I know that Breezy installs the 1.0.6. version of the ipw2200 by default and I also know that many people are having real problems with that version. So logically I need to upgrade the driver to the stable 1.1.0 version. This means I have to upgrade the firmware on my card and the ieee80211 subsystem. 

I have tried various ways of doing this, following directions from friendly people in the Ubuntu community
[http://doc.gwos.org/index.php/Install_ipw2200](http://doc.gwos.org/index.php/Install_ipw2200)
[http://www.ubuntuforums.org/showthread.php?t=154615](http://www.ubuntuforums.org/showthread.php?t=154615)

Now I'm in real trouble because I wanted to try once more and failed. Here is the output from terminal:

goonie@goonielap:~/download/ieeetmp/ieee80211-1.1.13$ make
Checking in /lib/modules/2.6.12-10-386 for ieee80211 components...
find: /lib/modules/2.6.12-10-386/build/: No such file or directory
/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ieee80211/ieee80211.ko
/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ieee80211/ieee80211_crypt_wep.ko
Above files found. Remove? [y],n y
find: /lib/modules/2.6.12-10-386/build/: No such file or directory
rm: cannot remove `/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ieee80211/ieee80211_crypt.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ieee80211/ieee80211.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ieee80211/ieee80211_crypt_ccmp.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ieee80211/ieee80211_crypt_tkip.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ieee80211/ieee80211_crypt_wep.ko': Permission denied
Old ieee80211 references found. In order to build the ieee80211
subsystem, prior versions must first be removed. You can perform
this task by running this makefile as root via:

% sudo make check_old

and answering Y to remove the file references.
Aborting make.
make: *** [check_old] Error 1

goonie@goonielap:~/download/ieeetmp/ieee80211-1.1.13$ sudo make check_old

Checking in /lib/modules/2.6.12-10-386 for ieee80211 components...
find: /lib/modules/2.6.12-10-386/build/: No such file or directory
/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ieee80211/ieee80211.ko
/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ieee80211/ieee80211_crypt_wep.ko
Above files found. Remove? [y],n y
find: /lib/modules/2.6.12-10-386/build/: No such file or directory
grep: /lib/modules/2.6.12-10-386/build//.config: No such file or directory
grep: /lib/modules/2.6.12-10-386/build//include/linux/autoconf.h: No such file or directory


Then I panicked (hehe) and didn't know what to do so I tried 'make' again

goonie@goonielap:~/download/ieeetmp/ieee80211-1.1.13$ make
Checking in /lib/modules/2.6.12-10-386 for ieee80211 components...
find: /lib/modules/2.6.12-10-386/build/: No such file or directory
grep: /lib/modules/2.6.12-10-386/build//.config: No such file or directory
grep: /lib/modules/2.6.12-10-386/build//include/linux/autoconf.h: No such file or directory
make -C /lib/modules/2.6.12-10-386/build M=/home/goonie/download/ieeetmp/ieee80211-1.1.13 modules
make: *** /lib/modules/2.6.12-10-386/build: No such file or directory. Stop.
make: *** [modules] Error 2

Then I thought to myself that all the errors were related to the missing /lib/modules/2.6.12-10-386/build directory and maybe that was for different distros and I shouldn't worry. So I tried 'make install' and got this.

goonie@goonielap:~/download/ieeetmp/ieee80211-1.1.13$ make install
make -C /lib/modules/2.6.12-10-386/build M=/home/goonie/download/ieeetmp/ieee80211-1.1.13 modules
make: *** /lib/modules/2.6.12-10-386/build: No such file or directory. Stop.
make: *** [modules] Error 2

So now I have no working ieee80211 on my system and don't know what to do. Can anyone walk me through this? I'm desperate! I need to upgrade/repair the followin: ieee80211 , ipw2200 and the firmware for the intel 2200GB card

Thx guys
Goonie

---

### Post by rabidphage on 2006-04-12
there is something inherently wrong with wireless in ubuntu. it randomly refuses to connect to the internet in a wifi busy enviornment.
i dont know how to prove this conclusively coz it connects to the router but some how fails to go beyond that..
if u r in a busy enviornment, keep an eye for that.
i've broken my install around 15 times in the past two months already....
This is the only reason i can see..

---

### Post by Jason_25 on 2006-04-12
[QUOTE=rabidphage]there is something inherently wrong with wireless in ubuntu. it randomly refuses to connect to the internet in a wifi busy enviornment.
[/QUOTE]
That's a pretty big generalization.  You'll need to post your specs if you want help.

---

### Post by rabidphage on 2006-04-12
i'm posting from windows now. I can't connect from ubuntu..randomly it connects. i'm a noob so please give me the commands and i will update here
thanks

---

### Post by Jason_25 on 2006-04-12
If you don't know your system specs, please contact your administrator or whoever built your computer.

---

### Post by rabidphage on 2006-04-12
i know the specs sorry about that.
intel 2200 B/G on ipw2200
But i don't think thats the problem coz i can connect to the ap
its something else probably related to obtaining lease or something
haven't got a clue
 I thought you needed the output of commands like ifconfig, iwconfig and stuff like that 
They look normal to me.
just wanted to know if there is a more specific trouble shooting command or things like that. I kinda know about networks and stuff but i'm not familiar with the commands and stuff like that.
thanks

---

### Post by pitkali on 2006-04-12
**Goonie:** You do have linux kernel sources installed and configured to match your running kernel, don't you?

**rapidphage:** That's strange what you say about something being **inherently** wrong. I have Intel 2200BG in my laptop and have no problems at home or university. Well, sometimes my laptop refuses to suspend to disk, but I'm not sure it's the network to blame. Apart from the situations where I know it's how HAL handles my printer ;) That's another story though.

Regards,

---

### Post by Goonie on 2006-04-13
I managed to get it to work :-D 

After finally getting everything installed I still couldn't get wireless working so I tried replacing the router and voilá......

so the latest ieee80211 subsystem, ipw2200-1.1.0 and the 2.4 version of the firmware along with a new router seems to have made the difference. The router is using the same firmware as before so that wasn't the problem.. The router was probably faulty to begin with :( 

thx for the help guys

Goonie

---

### Post by rabidphage on 2006-04-13
To me everything looks fine.. What do u guys think?????


darx@darx:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:CE:3C:CE:3C
          inet addr:172.25.26.199  Bcast:172.25.26.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe3c:ce3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1080 errors:0 dropped:9 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:122142 (119.2 KiB)  TX bytes:2848 (2.7 KiB)
          Interrupt:11 Base address:0xe000 Memory:c820b000-c820bfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

darx@darx:~$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11b  ESSID:"wolfradiolan"
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:0D:65:48:79:65
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=72/100  Signal level=-57 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.

darx@darx:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.25.26.0     *               255.255.255.0   U         0 0          0 eth0

---

### Post by krismatth3 on 2006-04-13
I have an Intel 2200BG in my laptop - no problems at all in Ubuntu.

---

### Post by pitkali on 2006-04-13
**rapidphage**: where's your gateway in routing table?

Regards,

---

### Post by rabidphage on 2006-04-13
[QUOTE=pitkali]**rapidphage**: where's your gateway in routing table?

Regards,[/QUOTE]

yes where is it???

i kinda solved it
[http://ubuntuforums.org/showthread.php?t=158659](http://ubuntuforums.org/showthread.php?t=158659)
maybe its the random automatic fix. i was tempted to beleive that i found a fix quite a few times..](*,)

---

