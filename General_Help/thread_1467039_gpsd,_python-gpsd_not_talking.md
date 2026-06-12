---
title: "gpsd, python-gpsd not talking"
date: 2010-04-30
forum: General Help
---

### Post by Gorlist on 2010-04-30
Hi, im running the latest ubuntu 10.04 32bit - so far so good however im having problems getting the program GmapCatcher ([http://code.google.com/p/gmapcatcher/](http://code.google.com/p/gmapcatcher/)) to use my gps bluetooth dongle. 

The dongle itself appears to be working, as xgps is running fine - however im having to start the service using sudo otherwise im getting permission denied: 

```
sudo service gpsd stop
sudo rfcomm connect 4
sudo gpsd -D 5 -nN /dev/rfcomm4
```

Im sure I had this problem in 9.10, and in the end I had to edit the user group permissions (to allow my username to read gpsd) to get GmapCatcher working, but for the life of me I can't find the original topic, so somewhat at a loss. 

Unfortunately im somewhat time limited as im taking the laptop away this Sunday on holiday! so anyhelp would be most appreciated.

Best Regards,

---

### Post by Gorlist on 2010-05-01
right just to update the post, ive done some further testing and the gps is certainly working. xgps and gpspipe -r is getting data, however any programs I try and use such as gpsdrive etc aren't?

---

### Post by YogiPaolo on 2010-05-10
I am in the same boat. I have the Garmin Gps 18 USB (the hockey puck).

I have to load the garmin_gps driver, which is not recommended but which is the only way 1. that the receiver is recognized and 2. that the receiver puts out data.

Running gpsd from the cli yields output with my locagpsd process start manuallytion. I was able to cut out the coordinates from the output, paste it in google maps and find exactly where I am. Cgps and xgps show 11 or 12 satellites recognized, but interestingly, a message says "no fix". This I do not understand. If my lat and long are somewhere in the stream, then why can't tangogps, gpsdrive, navit, xgps and cgps show now fix? 

So.... WTF...

This also seems to be a subject that nobody on the forums wants to touch. I started a thread about my device and so far nobody has an answer (yes that's a cheap shot attempt to dare someone to fix the problem for me LOL...).

Anyway, I'm sure someone has a better clue than I.

What info can I give you that may help?

this is a line from gpspipe -R:
```

{"class":"TPV","tag":"75","device":"/dev/ttyUSB0","time":1273531260.000,"ept":0.005,"lat":38.928980827,"lon":-77.072084052,"alt":78.690,"track":0.0000,"speed":0.000,"climb":0.000,"mode":1}
```

This clearly shows an accurate lat/long reading. Where is the breakdown!? 

The lack of documentation is pissing me off. As soon as we find a solution, i'm going on an information spreading campaign. LOL. My burning goal is to get this thing running so I can record GPS tracks of my weekend motorcycle trip to skyline drive.

---

### Post by ben_l on 2010-05-12
I'm seeing almost the exact same thing.  I can run gpsd and see it get coordinates, xgps and gpspipe -r work, yet gpsdrive and kismet show no GPS data when I try them.  Also, if I connect to gpsd on port 2947 and issue commands, there is no response, though I'm not sure if that indicates a real problem, since xgps and gpspipe give me coordinates.  I've been looking at this for two days.  All configs seem correct, but I'm out of ideas now.

---

### Post by Directive 4 on 2010-05-12
> **Gorlist said:**
> Hi, im running the latest ubuntu 10.04 32bit - so far so good however im having problems getting the program GmapCatcher ([http://code.google.com/p/gmapcatcher/](http://code.google.com/p/gmapcatcher/)) to use my gps bluetooth dongle. 

The dongle itself appears to be working, as xgps is running fine - however im having to start the service using sudo otherwise im getting permission denied: 

```
sudo service gpsd stop
sudo rfcomm connect 4
sudo gpsd -D 5 -nN /dev/rfcomm4
```Im sure I had this problem in 9.10, and in the end I had to edit the user group permissions (to allow my username to read gpsd) to get GmapCatcher working, but for the life of me I can't find the original topic, so somewhat at a loss. 

Unfortunately im somewhat time limited as im taking the laptop away this Sunday on holiday! so anyhelp would be most appreciated.

Best Regards,




update for 10.04

. type 
ps -C gpsd -fww


  output 
UID                  .....PID  PPID  C STIME TTY          TIME CMD
nobody 3993     1  0 17:16 ?        00:00:00 gpsd -N -n -D 2   /dev/ttyUSB0

we see that gpsd is running under nobody, lets kill it
sudo pkill gpsd

  start it up again but runing under your login not   nobody type
gpsd -N -n -D 2 /dev/ttyUSB0

6. open tango gps

7. ?????????

8. profit!





umm " I had to edit the user group permissions", i might try that now....

---

### Post by ben_l on 2010-05-12
I don't think it's a permissions issue for me.  I have gpsd running as root.

---

### Post by Directive 4 on 2010-05-12
> **ben_l said:**
> I don't think it's a permissions issue for me.  I have gpsd running as root.


this also is not good, try kill it then 

gpsd -N -n -D 2 /dev/ttyUSB0

---

### Post by YogiPaolo on 2010-05-13
Last night I saw profit. Cgps showed an accurate date (instead of midnight in 1970...). On a rainy day indoors, I got a fix that was within 300 feet. Today I get NOTHING.

What I thought fixed the issue was running: gpsctl -n

After I did that, restarted gpsd, I suddenly got a fix in cgps. Tangogps showed my location on the map. Doing all this today yields NOTHING. So i'm guessing now that it was a random success and that i should go back to square 1.

I notice that I do not have a "gpsd" or "gps" group. Should I? What groups should my user be a member of to get gpsd data?

Maybe this is the issue...

---

### Post by YogiPaolo on 2010-05-13
This is a quote from the gpsd documentation:

> Security And Permissions Issues

gpsd must start up as root in order to open the NTPD shared-memory segment, open its logfile, and create its local control socket. Before doing any processing of GPS data, it tries to drop root privileges by setting its UID to "nobody" (or another userid as set by configure) and its group ID to the group of the initial GPS passed on the command line -- or, if that device doesn't exist, to the group of /dev/ttyS0.


Could it be that gpsd is having trouble with NTP? Something that seems a clue to me is the fact that cgps shows a time of " 1970-01 -01T00..."

---

### Post by ben_l on 2010-05-13
Do you know what's different about xgps/gpspipe accessing gpsd data and other programs?  I'm a little confused as to how xgps and gpspipe can get coordinates, but nothing else I try works.

---

### Post by NDLunchbox on 2010-05-14
Hey guys,
I spent a few hours researching this last night, found some very useful threads and after a lot of trial and error, found the following:

gpsd under went some major changes recently and the newer version (2.92 on my 10.04 AMD64) no longer recognizes some of the commands / data formats used by the version of gpsdrive in the repository.

I did the following to get my USB Garmin etrex working:

1) used dkpg to reconfigure gpsd not to start automatically
2) unblacklisted the Garmin USB entry in /etc/modprob.d/blacklist.conf
3) rebooted and started gpsd in a terminal with $ gpsd -nND 2 /dev/ttyUSB0
At this point I could see gps data streaming in the terminal.  xgps, tangogps and the newest version of Kismet (compiled from source) all worked.  Still no love from gpsdrive.

I tried compiling the latest stable release of gpsdrive from source.  Very painful and no luck, I even tried updating some of the gpsd calls to the new formats in the source as per a thread I found, almost got it to compile, but did not install it.

Apparently the issues have been fixed in the SVN version.  I tried installing the ubuntu package, but it's only 32-bit.  I'm thinking of reporting a bug on the incompatibility.

At this point, I'm waiting for gpsdrive ver. 11, should be out soon I hope!

edit - ps, the 'r' command has been deprecated, so if you telnet in, issue it and see nothing - it doesn't mean gpsd isn't working.

Here is the thread I found that was packed with info... [http://comments.gmane.org/gmane.comp.linux.gps/5555]("http://comments.gmane.org/gmane.comp.linux.gps/5555")

---

