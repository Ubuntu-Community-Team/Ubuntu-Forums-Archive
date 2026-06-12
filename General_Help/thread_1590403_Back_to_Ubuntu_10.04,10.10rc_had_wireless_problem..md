---
title: "Back to Ubuntu 10.04,10.10rc had wireless problem."
date: 2010-10-07
forum: General Help
---

### Post by jvhellraiser on 2010-10-07
well I had format my disk drive and install a fresh copy of Ubuntu 10.04 after that i download it Ubuntu 10.10 rc.iso because at first i thought that upgrading from Ubuntu 10.04 to 10.10 rc and there was a problem with the upgrade so this time i download it and burn it to a cd and boot it in live cd but with the same mistake or problem of wireless network now i know the problem wasn't the upgrade,so this is what happens:

1.I have a d-link network wireless card pci DWL-650m1.
2.I can see the wireless icon on my desktop but i can't create and it wont
detect my wireless connection directly is like is not even there if i try to create with new wireless network then it connects thought when i disconnect the wireless disappear and i have to enter new wireless connection to connect again but even know is connected or at least thats what it says i can access the internet is like my wireless card is a ghost
or ubuntu is bloking it someway.any ideas?

if you want more info please ask me couse iam new to this.

buy the way iam at ubuntu 10.04 now this only happens with ubuntu 10.10 rc.

---

### Post by Awareness on 2010-10-07
first, you can use unetbootin to live usbs. More practical than live cds ;)

sudo apt-get install unetbootin

If your wireless works ok with ubuntu 10.04, just stick to it until you can verify it works on 10.10. Wait till the final releases tho. rc are known for lots of stuff not working as expected... i learned this after many, many, many unsuccessful upgrades :)

Report the bug to launchpad if its not been reported already.

Sorry if this is just general advice. Wifi can be tough on linux sometimes and i am not very fond on it.

Anyway, i didnt understand what you mean by not finding your wireless icon on desktop

what is the output of ifconfig -a?

---

### Post by Dex73 on 2010-10-07
Your not alone jvhellraiser. The first ubuntu I ever installed wouldn't work on my computer. Any time 9.10 would try to connect to the internet at college, they had WPA security, it would freeze to the extent that I would have to shut it down hard.(Not good on my hard drive!) This didn't happen with an ether net cable and home network that has no security worked fine. I switched to 8.04 and it fixed the problem. Sometimes the small tweaks made in the ubuntu versions cause trouble. 10.04 has also been working great for me.

---

### Post by Awareness on 2010-10-07
> **Dex73 said:**
> Your not alone jvhellraiser. The first ubuntu I ever installed wouldn't work on my computer. Any time 9.10 would try to connect to the internet at college, they had WPA security, it would freeze to the extent that I would have to shut it down hard.(Not good on my hard drive!) This didn't happen with an ether net cable and home network that has no security worked fine. I switched to 8.04 and it fixed the problem. Sometimes the small tweaks made in the ubuntu versions cause trouble. 10.04 has also been working great for me.

In my experiencie, these freezes are due to wpa_supplicant, that is the wpa negotiation of your wireless. Usually wep negotiation or no negotiation works fine. In this cases you can try to connect to a wep wireless to find out if that works. I had to recompile the module of my wireless card because it hasn't had wpa supplicant by default. Dont know why. In latest ubuntu it works fine without any tweking :)

That being said, stick to the versions that works if you dont want to hack anything :). Wireless under linux really is a pain sometimes

---

### Post by jvhellraiser on 2010-10-07
Awareness,is not that i don't see the wireless icon on the desktop
i can see it but it wont do anything like sniff my wireless network
and if try to add one with the option (create new wireless network)
I'll connect to it but when i open the browser it says differently
is like Ubuntu is connected to something or at least try but it wont 
grab no packages.oh one more thing when i disconnect the wireless 
network it disappear and you'll have to do (create new wireless network) AGAIN!!!
but it wont matter cause it wont connect anyway so i'll stay with 10.04
until they fix this problem. Thanks for your help guys 

i have try to explain the best i can because my main language is Spanish
so sorry if i made some mistakes in the words i have write.

Here is what you want it Awareness

this is from Ubuntu 10.10 rc

eth0      Link encap:Ethernet  HWaddr 00:0b:6a:0d:91:4f  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:23 Base address:0xcd00 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:72 errors:0 dropped:0 overruns:0 frame:0

          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:5552 (5.5 KB)  TX bytes:5552 (5.5 KB)



wlan0     Link encap:Ethernet  HWaddr 00:0d:88:c8:5d:74  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


and this one is from Ubuntu 10.04

eth0      Link encap:Ethernet  HWaddr 00:0b:6a:0d:91:4f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xd00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0d:88:c8:5d:74  
          inet addr:10.0.0.68  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:88ff:fec8:5d74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15383 (15.3 KB)  TX bytes:12952 (12.9 KB)

hope this works for something.

---

