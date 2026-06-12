---
title: "how do you restart a process?"
date: 2011-08-08
forum: General Help
---

### Post by sdowney717 on 2011-08-08
like gpsd?
I looked around and people talk about manually starting but dont say what the command is.

---

### Post by haqking on 2011-08-08
> **sdowney717 said:**
> like gpsd?
I looked around and people talk about manually starting but dont say what the command is.

gpsd start or

/etc/init.d/gpsd start

---

### Post by sdowney717 on 2011-08-08
thanks I guess I dont know if it is working

gpsd start just returns a new line in terminal

/etc/init.d/gpsd start No such file or directory

how would you restart gpsd?


scott@scott-P5QC:~$ gpsd
gpsd: can't run with neither control socket nor devices
scott@scott-P5QC:~$ gpsd restart
scott@scott-P5QC:~$ gpsd stop
scott@scott-P5QC:~$ gpsd start
scott@scott-P5QC:~$ etc/init.d/gpsd start
bash: etc/init.d/gpsd: No such file or directory
scott@scott-P5QC:~$ 

When I unplug the gps, and plug it back in, gpsd does nothing.
when I boot with the gps plugged in, gpsd works

---

### Post by haqking on 2011-08-08
> **sdowney717 said:**
> thanks I guess I dont know if it is working

gpsd start just returns a new line in terminal

/etc/init.d/gpsd start No such file or directory

how would you restart gpsd?


scott@scott-P5QC:~$ gpsd
gpsd: can't run with neither control socket nor devices
scott@scott-P5QC:~$ gpsd restart
scott@scott-P5QC:~$ gpsd stop
scott@scott-P5QC:~$ gpsd start
scott@scott-P5QC:~$ etc/init.d/gpsd start
bash: etc/init.d/gpsd: No such file or directory
scott@scott-P5QC:~$ 

When I unplug the gps, and plug it back in, gpsd does nothing.
when I boot with the gps plugged in, gpsd works

ps 

is the command to see what processes are running on a system so you can see if it is working

man ps

to see what switches for whatever results you want it to return

---

### Post by blueridgedog on 2011-08-08
If gpsd is a service with a system service config, you can use:

```
$ sudo service gpsd restart <-- Restart service
$ sudo service gpsd stop <-- Stop service
$ sudo service gpsd start <-- Start service
```

If it is simply an application, you can:

killall gpsd <-- Stop application
/path/to/gpsd <-- Start application (replace path as needed)

---

### Post by sdowney717 on 2011-08-08
thanks blueridgedog, that did a restart of gpsd

```
scott@scott-MS-7104:~$ sudo service gpsd restart
[sudo] password for scott: 
 * Restarting GPS (Global Positioning System) daemon gpsd                [ OK ] 
scott@scott-MS-7104:~$ xgps

```

what i need is someone to tell me how to make gpsd receive data after you unplug the gps and then plug it back in. I was hoping restart would work but still gpsd displays no data. The device port is active and the gps is working. 

here is a shot showing /dev/ttyUSB0 getting data from the gps and gpsd not getting data
to clarify, on a fresh boot, gpsd works and gets data, but if you unplug the gps and then plug it back in, gpsd does not work again until you reboot.
I was hoping a gpsd restart would make it work but it did not.

---

### Post by sdowney717 on 2011-08-08
actually the whole process is kinda flaky. really the usb gps is only working well on a boot up. Unplug then replug and it takes a very long time to aquire a fix, if it ever does.

(Ok, it just got a fix after 10 minutes. on a boot it gets a fix in a minute)

So I dont know. Somehow the unplugging screws it up and then replugging it does not know quite what to do.
But if it boots then the gps gets a quick position fix.
So what would be running at boot that makes it work and what is not running on a replug that keeps it from working?

---

### Post by sdowney717 on 2011-08-08
cat the device on a boot with the device plugged in and you get data
```
scott@scott-MS-7104:~$ cat /dev/ttyUSB0
$GPRMC,004212.000,A,3707.924,N,07634.197,W,0.0,0.0,090811,11.1,W*58
$GPGGA,004212.000,3707.92436,N,07634.19741,W,1,06,1.7,016.55,M,-34.3,M,,*50
$GPVTG,0.0,T,348.9,M,0.0,N,0.1,K*49
$GPGSV,3,1,11,02,47,272,35,04,70,011,43,05,17,202,00,09,06,259,00*7D
$GPGSV,3,2,11,10,61,159,41,12,32,311,32,13,11,093,00,17,52,095,40*77
$GPGSV,3,3,11,20,06,040,00,23,11,066,32,28,09,162,00,,,,*4F
$PSTMECH,10,7,02,7,12,7,00,0,00,0,17,7,00,0,23,7,04,7,00,0,00,0,00,0*57

```

cat the device when unplug then replug and this is what you get
```
scott@scott-MS-7104:~$ cat /dev/ttyUSB0
GPRMC,005518.000,A,3707.928,N,07634.199,W,0.0,0.0,090811,11.1,W*56
$GPGGA,005518.000,3707.92781,N,07634.19862,W,1,08,1.8,011.91,M,-34.3,M,,*53
$GPVTG,0.0,T,348.9,M,0.0,N,0.0,K*48
$GPGSV,3,1,09,02,51,279,31,04,66,024,45,05,23,203,00,10,67,151,35*7F
$GPGSV,3,2,09,12,36,306,27,13,14,087,39,17,47,102,39,23,12,060,31*7F
$GPGSV,3,3,09,25,07,325,34,,,,,,,,,,,,*43
$GPGSA,A,3,17,04,10,02,12,13,23,25,,,,,2.5,1.8,1.7*3C
scott@scott-MS-7104:~$ 

```

---

### Post by sdowney717 on 2011-08-09
I did a purge on gpsd (plus)
and then did updates

reinstalled and reconfigure gpsd and it seems to be working like it should.
disconnect reconnect is working
so go figure.

---

### Post by blueridgedog on 2011-08-09
> **sdowney717 said:**
> I did a purge on gpsd (plus)
and then did updates

reinstalled and reconfigure gpsd and it seems to be working like it should.
disconnect reconnect is working
so go figure.

Interesting...I can't see a reason where something would cause it to work, but be slow and that it would be corrected by a purge and reinstall.  Perhaps there is no cache data at boot and there is on a reset?

---

