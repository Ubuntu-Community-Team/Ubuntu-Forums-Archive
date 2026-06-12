---
title: "How to repair broken packages on HDD from Livecd"
date: 2010-05-03
forum: General Help
---

### Post by asuastrophysics on 2010-05-03
Hey all,

As a suggested fix to solve a problem with cairo-dock, on 5/2/10 at 11:00pm, I ran the following in a 9.10 terminal window:
```
sudo apt-get dist-upgrade
```

This somehow deleted all of my kernel images, and a bunch of other files.
I'm running the livecd now. Is there any way to run dpkg from the livecd on my mounted HDD? I can't access anything while booting up the HDD except for memtest in the grub, so going into recovery mode is impossible.

I hope my question makes sense. Can anyone help me??

Thanks a TON in advance. 
My computer is just a giant paperweight right now :(

---

### Post by nanog on 2010-05-03
click on the blue chroot link in my sig. let me know if you have problems (sometimes extra commands are necessary for network access).

---

### Post by asuastrophysics on 2010-05-03
> **nanog said:**
> click on the blue chroot link in my sig. let me know if you have problems (sometimes extra commands are necessary for network access).

Awesome! thanks! So that chroot command worked. Now I just need to figure out how to connect to a wifi network manually:
```
iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:26:F2:E1:C4:8A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:off
                    ESSID:"NETGEAR-2.4-G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002c472824955
                    Extra: Last beacon: 620ms ago
                    IE: Unknown: 000D4E4554474541522D322E342D47
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A00011010440001011041000100103B00010310470010F33E0F2EC7E1AC143B504307D79E0A9C1021000D4E4554474541522C20496E632E10230008574E44523333303010240008574E4452333330301042000230311054000800060050F204000110110008574E445233333030100800020084103C000103
                    IE: Unknown: DD090010180203F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```

That network there, "Netgear2.4", is an unsecured network that I need to connect to (I made it unsecure because I believe this makes it easier to connect to). So what commands should I issue to connect to it? BTW Thanks for your help!

---

### Post by asuastrophysics on 2010-05-03
figured out the internet issue by using this page:
[http://lukeplant.me.uk/blog/posts/sharing-internet-connection-to-chroot/](http://lukeplant.me.uk/blog/posts/sharing-internet-connection-to-chroot/)

now, i just need to basically reinstall everything the update-manager decide to screw up. wish me luck!!! i didn't even know about CHROOT before you mentioned it to me, thanks!

---

### Post by asuastrophysics on 2010-05-03
Thank you so much for your reply. I was able to run:
```
sudo apt-get install -f
```
then:
```
sudo apt-get install linux-kernel-generic
```

and fix most of my problems after the CHROOT thing. I looked up online how to prepare my HDD for using CHROOT (essential!), then issued the following commands above to fix my broken packages. I then updated to grub2 from grub legacy, because with grub legacy, I ran into the following at boot when I selected my new kernel:
```
Error 11: Unrecognized Device String
```
upgrading to grub2 alleviated these issues. I am currently back on the HDD partition, upgrading to 10.4LTS 

Thanks, once again, for your help! :D
Thread -> Solved

---

