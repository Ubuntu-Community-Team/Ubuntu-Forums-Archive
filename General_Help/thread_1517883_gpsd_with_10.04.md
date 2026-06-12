---
title: "gpsd with 10.04"
date: 2010-06-25
forum: General Help
---

### Post by jean_christophe on 2010-06-25
Hello

I have post this question on the french forum, but didn't get an answer.
I have installed gpsd, gpsd-client & gpsdrive through the software manager.

I have a gps from Earthmate LT-20.
The GPS is running fine. the problem is that I can see nothing on xgps nor gpsdrive!

I know that the gps is working, because when I do:
```

cat /dev/ttyUSB0

```
I can see those lines:
```

$GPRMC,065839.000,V,5526.763,N,01149.589,E,1.9,268.2,230610,0.0,E*71
$GPGGA,065839.000,5526.76310,N,01149.58865,E,0,01,99.0,064.79,M,42.8,M,,*53
$GPGSV,3,1,12,02,38,296,00,04,48,233,27,05,03,297,00,07,33,177,00*7F
$GPGSV,3,2,12,08,03,193,00,10,34,292,00,13,85,094,00,16,18,063,00*7D
$GPGSV,3,3,12,20,19,123,00,23,57,074,00,29,05,355,00,32,00,114,00*78
$GPGSA,A,1,04,,,,,,,,,,,,99.0,99.0,99.0*04

```

I (try to) start gpsd like this:
```

gpsd /dev/ttyUSB0

```

If I use top, I can see that it is working
```

 923 root      20   0 45720  17m 9464 S    3  0.9   4:27.96 Xorg                  
 2174 christop  20   0  128m  30m  21m S    1  1.5   0:34.15 konsole               
 1407 christop  20   0 51308  13m  10m S    1  0.7   0:11.69 wnck-applet           
 2620 christop  20   0 87324  15m  11m S    1  0.8   0:14.65 tangogps              
 2711 christop  20   0  2544 1224  920 R    1  0.1   0:00.07 top                   
  990 nobody    10 -10  5064 2216  948 S    0  0.1   0:01.95 gpsd                  
 1289 christop  20   0 67856  23m 7864 S    0  1.2   0:37.35 compiz                
 1539 christop  20   0 31804  18m 4184 S    0  0.9   0:13.99 ubuntuone-syncd

```

But when I start xgps, I have a message telling me that gpsd is not running!

If I try to run this command:
```

christophe@asus:~$ gpsd -F /dev/ttyUSB0

```
It's returns me this:
```

gpsd: can't listen on local socket /dev/ttyUSB0
gpsd: control socket create failed, netlib error -1

```

I think that it is the main problem, because I made this command as root on a mandriva machine and I could see xgps showing me some gps.

Can you tell me how I could fix this error?

```

gpsd: can't listen on local socket /dev/ttyUSB0
gpsd: control socket create failed, netlib error -1

```

---

### Post by Spr0k3t on 2010-06-27
Bonjour Jean-Christophe,

The problem c'est facile to troubleshoot.  I used this information to track down the issues I had and ensure the functionality was there on every boot for one of my computer systems.  Once you have reconfigured the gpsd, you should not need to use the -F to get communication working correctly.  Bonne chance.

[http://ubuntuforums.org/showthread.php?t=1200497](http://ubuntuforums.org/showthread.php?t=1200497)

---

### Post by jean_christophe on 2010-06-28
Ca marche!
It's working, super

Thank you very much
Can you use the "reconfigure" option for all packages?

---

### Post by Spr0k3t on 2010-06-28
C'est bien!  I'm not sure about the reconfigure option for all packages, but I've used it on many different occaisions myself.  Most of the packages are daemons like lcdproc, lirc, gpsd, mpd etc.  Mais tu ne pense pas c'est possible?  Qui sait.

(having not used french in quite a while, I'm amazed at how much I still remember... lol).

---

### Post by jean_christophe on 2010-06-28
Je pensais que tu étais francais!
Tu te débrouilles toujours bien.
Si tu ne veux pas "perdre la main" tu peux toujours aller lá: [http://www.ubuntu-fr.org/](http://www.ubuntu-fr.org/)

A bientôt

---

