---
title: "Lt-20 Delorme GPS how to make work in Ubuntu?"
date: 2011-08-06
forum: General Help
---

### Post by sdowney717 on 2011-08-06
> [1013333.752031] usb 7-1: new full speed USB device using uhci_hcd and address 3
[1013333.939089] cypress 7-1:1.0: DeLorme Earthmate USB converter detected
[1013333.940128] usb 7-1: DeLorme Earthmate USB converter now attached to ttyUSB0


this is working in win7 and from forum posts I read LT20 bug was fixed in 2.6.26 kernel 
I installed gpsd
I noticed in the Delorme program, I had to click start GPS to get it to start, so how to do this in linux?

Delorme offers a serial emulator to control the device in windows.

[http://forum.delorme.com/viewtopic.php?t=12216](http://forum.delorme.com/viewtopic.php?t=12216)
> 
The bottom line is that the new 2.6.26 kernel properly supports all 4 of these USB-based DeLorme Earthmate GPS receivers. 

My sincere thanks to Mike Isely for providing these very useful patches and pushing them upstream for kernel inclusion! He did all the hard work -- all I did was test and report. 

Hopefully this will be useful to all you Linux-loving Earthmate GPS users, like me! :^) 


I did find a comment to cat the port it makes and I get this as output
so is it outputting the data? I think so, the red blinking light is blinking green so it has a 3d lock.

```
scott@scott-P5QC:~$ cat /dev/ttyUSB0 
$PSTMVER,GPS Version 4.20.5 Release ARM (15:52:14 Feb  4 2005),0x8C0B
$GPRMC,192632.000,V,3707.923,N,07634.197,W,0.0,0.0,060811,11.1,W*4F
$GPGGA,192632.000,3707.92322,N,07634.19719,W,0,00,99.0,005.40,M,-34.3,M,,*60
$GPVTG,0.0,T,348.9,M,0.0,N,0.0,K*48
$GPGSV,3,1,10,03,13,055,00,07,78,212,00,08,63,310,00,11,59,133,00*70
$GPGSV,3,2,10,13,10,199,00,17,06,235,00,19,43,045,00,24,40,145,00*73
$GPGSV,3,3,10,26,11,317,00,28,30,297,00,,,,,,,,*7C
$PSTMECH,00,0,00,0,00,0,00,0,00,0,00,0,00,0,00,0,00,0,00,0,00,0,00,0*54
$GPRMC,192633.000,V,3707.923,N,07634.197,W,0.0,0.0,060811,11.1,W*4E
$GPGGA,192633.000,3707.92322,N,07634.19719,W,0,00,99.0,005.40,M,-34.3,M,,*61
$GPVTG,0.0,T,348.9,M,0.0,N,0.0,K*48
$GPGSV,3,1,10,03,13,055,00,07,78,212,00,08,63,310,00,11,59,133,00*70
$GPGSV,3,2,10,13,10,199,00,17,06,235,00,19,43,045,00,24,40,145,00*73
$GPGSV,3,3,10,26,11,317,00,28,30,297,26,,,,,,,,*78
$GPGSA,A,1,,,,,,,,,,,,,99.0,99.0,99.0*00
$GPRMC,194125.000,A,3707.918,N,07634.208,W,0.1,0.0,060811,11.1,W*53
$GPGGA,194125.000,3707.91829,N,07634.20824,W,1,04,4.6,020.57,M,-34.3,M,,*59
$GPVTG,0.0,T,348.9,M,0.1,N,0.2,K*4B
$GPGSV,3,1,09,03,08,058,00,07,72,195,36,08,69,299,35,11,63,119,27*74
$GPGSV,3,2,09,17,11,238,00,19,37,046,00,24,45,140,00,26,13,311,00*77
$GPGSV,3,3,09,28,34,302,28,,,,,,,,,,,,*46
$PSTMECH,07,7,08,7,11,7,00,0,00,0,28,7,00,0,00,0,00,0,00,0,00,0,00,0*51
$GPRMC,194126.000,A,3707.918,N,07634.208,W,0.2,0.0,060811,11.1,W*53
$GPGGA,194126.000,3707.91831,N,07634.20823,W,1,04,4.6,020.63,M,-34.3,M,,*53
$GPVTG,0.0,T,348.9,M,0.2,N,0.4,K*4E
$GPGSV,3,1,09,03,08,058,00,07,72,195,36,08,69,299,34,11,63,119,28*7A
$GPGSV,3,2,09,17,11,238,00,19,37,046,00,24,45,140,00,26,13,311,00*77
$GPGSV,3,3,09,28,34,302,27,,,,,,,,,,,,*49
$GPGSA,A,3,07,08,11,28,,,,,,,,,6.8,4.6,5.1*3F
$GPRMC,194127.000,A,3707.918,N,07634.208,W,0.2,0.0,060811,11.1,W*52
$GPGGA,194127.000,3707.91832,N,07634.20822,W,1,04,4.6,020.64,M,-34.3,M,,*57
$GPVTG,0.0,T,348.9,M,0.2,N,0.3,K*49
$GPGSV,3,1,09,03,08,058,00,07,72,195,36,08,69,299,34,11,63,119,28*7A
$GPGSV,3,2,09,17,11,238,00,19,37,046,00,24,45,140,00,26,13,311,00*77
$GPGSV,3,3,09,28,34,302,29,,,,,,,,,,,,*47
$PSTMECH,07,7,08,7,11,7,00,0,00,0,28,7,00,0,00,0,00,0,00,0,00,0,00,0*51
$GPRMC,194128.000,A,3707.918,N,07634.208,W,0.3,72.7,060811,11.1,W*6E
$GPGGA,194128.000,3707.91839,N,07634.20810,W,1,04,4.6,020.65,M,-34.3,M,,*53
$GPVTG,72.7,T,61.6,M,0.3,N,0.5,K*4B
$GPGSV,3,1,09,03,08,058,00,07,72,195,36,08,69,299,35,11,63,119,28*7B
$GPGSV,3,2,09,17,11,238,00,19,37,046,00,24,45,140,00,26,13,311,00*77
$GPGSV,3,3,09,28,34,302,27,,,,,,,,,,,,*49
$GPGSA,A,3,07,08,11,28,,,,,,,,,6.8,4.6,5.1*3F
$GPRMC,194129.000,A,3707.918,N,07634.208,W,0.1,0.0,060811,11.1,W*5F
$GPGGA,194129.000,3707.91836,N,07634.20814,W,1,04,4.6,020.67,M,-34.3,M,,*5B
$GPVTG,0.0,T,348.9,M,0.1,N,0.2,K*4B
$GPGSV,3,1,09,03,08,058,00,07,72,195,36,08,69,299,34,11,63,119,27*75
$GPGSV,3,2,09,17,11,238,00,19,37,046,00,24,45,140,00,26,13,311,00*77
$GPGSV,3,3,09,28,34,302,28,,,,,,,,,,,,*46
$PSTMECH,07,7,08,7,11,7,00,0,00,0,28,7,00,0,00,0,00,0,00,0,00,0,00,0*51
$GPRMC,194130.000,A,3707.918,N,07634.208,W,0.1,0.0,060811,11.1,W*57
$GPGGA,194130.000,3707.91838,N,07634.20814,W,1,04,4.6,020.68,M,-34.3,M,,*52
$GPVTG,0.0,T,348.9,M,0.1,N,0.2,K*4B
$GPGSV,3,1,09,03,08,058,00,07,72,195,35,08,69,299,34,11,63,119,28*79
$GPGSV,3,2,09,17,11,238,00,19,37,046,00,24,45,140,00,26,13,311,00*77
$GPGSV,3,3,09,28,34,302,28,,,,,,,,,,,,*46
$GPGSA,A,3,07,08,11,28,,,,,,,,,6.8,4.6,5.1*3F
$GPRMC,194131.000,A,3707.918,N,07634.208,W,0.0,0.0,060811,11.1,W*57
$GPGGA,194131.000,3707.91838,N,07634.20816,W,1,04,4.6,020.72,M,-34.3,M,,*5A
$GPVTG,0.0,T,348.9,M,0.0,N,0.0,K*48
$GPGSV,3,1,09,03,08,058,00,07,72,195,35,08,69,299,34,11,63,119,28*79
$GPGSV,3,2,09,17,11,239,00,19,37,046,00,24,45,140,00,26,13,311,00*76
$GPGSV,3,3,09,28,34,302,29,,,,,,,,,,,,*47
$PSTMECH,07,7,08,7,11,7,00,0,00,0,28,7,00,0,00,0,00,0,00,0,00,0,00,0*51
$GPRMC,194132.000,A,3707.918,N,07634.208,W,0.0,0.0,060811,11.1,W*54
$GPGGA,194132.000,3707.91838,N,07634.20815,W,1,04,4.6,020.77,M,-34.3,M,,*5F
$GPVTG,0.0,T,348.9,M,0.0,N,0.0,K*48
$GPGSV,3,1,09,03,08,058,00,07,72,195,35,08,69,299,35,11,63,119,28*78
$GPGSV,3,2,09,17,11,239,00,19,37,046,00,24,45,140,00,26,13,311,00*76
$GPGSV,3,3,09,28,34,302,28,,,,,,,,,,,,*46
$GPGSA,A,3,07,08,11,28,,,,,,,,,6.8,4.6,5.1*3F
^C
scott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2011-08-06
ok, it has a fix in opencpn a boat charting program.

I dont know if true but, I tried this first on the ubuntu machine and the lt20 never stopped blinking red,
So I tried plugging it into a USB charger and it always blinked red
Then I tried it on a windows 7 machine and it got a fix when I said start gps in the delorme program. 
I then went back to the ubuntu machine and it worked.
Blinking red means acquiring sats.
Blinking yellow means 2D fix
Blinking green means 3D fix, it is blinking green on ubuntu.

Some forum poster mentioned you might have to if you moved the GPS far way, reinitialize location on windows??

For openCPN, I had to set the port and then the data comes up.
What program could i use for road navigation?

---

### Post by sdowney717 on 2011-08-06
I got GPSD configured. did a search and found the file and it says to run

sudo dpkg-reconfigure gpsd

so, I did and did a reboot and now gpsd is working and passing gps position data to FoxtrotGPS
gpsd you need to type in the port number for the gpd device. You can find it by plugging in the gps device, then type in dmesg.

---

### Post by sdowney717 on 2011-08-06
[http://wiki.networksecuritytoolkit.org/nstwiki/index.php/HowTo_Setup_The_NST_System_With_A_GPS_(gpsd](http://wiki.networksecuritytoolkit.org/nstwiki/index.php/HowTo_Setup_The_NST_System_With_A_GPS_(gpsd))

here are some interesting pages on gpsd including one that shows how to display satellite map your device has by running xgps

---

