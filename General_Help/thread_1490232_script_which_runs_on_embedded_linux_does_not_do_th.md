---
title: "script which runs on embedded linux does not do the same on Ubuntu"
date: 2010-05-22
forum: General Help
---

### Post by benzan on 2010-05-22
Hi, all.
 
I'm busy making a web controlled radio transceiver. The transceiver is connected to a Bifferboard, by use of an USB-RS-232 convertor. Installed are the hamlib utils and python-hamlib, the radio receives it's commands from rigctl which is a part of these utils.  All works wel from the command line so the next step was to make it run from a script.
 
I did find an example how to run linux commands and programs from a script
 
[http://www.cyberciti.biz/tips/executing-linuxunix-commands-from-web-page-part-i.html](http://www.cyberciti.biz/tips/executing-linuxunix-commands-from-web-page-part-i.html)
 
 (the original application shows system info from the running system) to which I added a few lines to send data to the transceiver and read the frequency back and display it.
 
It works great, but now I had to create a webpage with buttons to send presets to the radio. For easier testing I got the advice to do the development on a normal system instead of by terminal on the bifferboard.
 
So, I fired up the Ubuntu 9.04 system, installed the hamlib utils and python-hamlib. Apache was allready running, cgi was enabled in apache. The example page from the website above was running fine. 
 
On this system I connected the same radio, tried to control the radio from the command line and it works great. Than I did run the same script as I was running on the Bifferboard, the system info shows up on the webpage but there is no frequency displayed from the transceiver.
 
The Bifferbaord is running Lighttp, so I installed this on the Ubuntu system on port 88, and enabled CGI for Lighttpd also. Unfotunately, the same thing happens. The page displays the information from my system, but not the data received from the radio.
 
From the command line however, I can control the transceiver with the commands I copy from the script file, so this should work. I did check the PATH on both the systems but they are right set.
 
Does anyone have any idea why the rigctl lines in the script do not work from the Ubuntu system but do work from the Bifferboard ?
 
Below I past the script and the screen output from the Ubuntu system.
 
Thanks,
Ben
 

#!/bin/bash 
echo "Content-type: text/html" 
echo "" 
echo "<html><head><title>Bash as CGI" 
echo "</title></head><body>" 

echo "General system information for host $(hostname -s)" 
echo "" 

echo "<h1>Memory Info</h1>" 
echo "<pre> $(free -m) </pre>" 

# echo "<h1>Disk Info:</h1>" 
# echo "<pre> $(df -h) </pre>" 

echo "<h1>Logged in user</h1>" 
echo "<pre> $(w) </pre>" 

echo "<pre> $(rigctl -m 120 -r /dev/ttyUSB0 --serial-speed=9600 F 
145750000 M FM 0) </pre>" 
/Here I set the Frequency to 145.750 and mode to FM 
echo "<h1> The FT-817 radio is tuned to this frequency:</h1>" 
echo "<pre> $(rigctl -m 120 -r /dev/ttyUSB0 -s 9600 f ) </pre>" 
echo "<pre> $(rigctl -m 120 -r /dev/ttyUSB0 -s 9600 get_mode ) </pre>" 
echo "<center>Information generated on $(date)</center>" 
echo "</body></html>" 

 
**[COLOR=navy]Page Output on Ubuntu:[/COLOR]**
**[COLOR=navy][/COLOR]** 

[B][COLOR=navy]General system information for host ontwikkeldoos 
Memory Info 
              total       used       free     shared    buffers 
cached 
Mem:          1500        531        968          0         29 
207 
-/+ buffers/cache:        293       1206 
Swap:         3239          0       3239 
Logged in user 
  20:44:16 up 35 min,  2 users,  load average: 0.00, 0.00, 0.00 
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT 
root     tty7     :0               20:09     ?    14.69s  0.15s gnome- 
session 
root     pts/0    :0.0             20:13    3:04   0.02s  0.02s bash 
[/COLOR][/B]**[COLOR=navy]The FT-817 radio is tuned to this frequency: [/COLOR]**
[B][COLOR=navy]
 
[/COLOR][/B]**[COLOR=navy]Information generated on Fri May 21 20:44:16 CEST 2010[/COLOR]** 
 
On the Bifferboard is shows 145750000 as frequency and 0 for the mode at the line above the last line.

---

### Post by jamesisin on 2010-05-22
My system (8.10) doesn't have the rigctl command and so any attempt to use that command will error.

You may also want to check your BASH versions to see if there is a version conflict which might interfere with your scripting.

---

### Post by gmargo on 2010-05-22
> Does anyone have any idea why the rigctl lines in the script do not work  from the Ubuntu system but do work from the Bifferboard ?

Probably permissions.  What are the permissions on the device?

---

### Post by benzan on 2010-05-22
> **gmargo said:**
> Probably permissions. What are the permissions on the device?
 
Learning every day. Permissions on the device ? I guess you mean the ttyUSB0 device ? I did not know that you can set permissions ther also.
 
In the meantime, from the Apache tutorial about Dynamic Content with CGI I learned that when I run the script with ./benno.cgi from the command line the transceiver gets tuned and the frequency is displayed. (I'm root at the command line)
 
Does that make sense in combination with your remark about the permissions ?
 
Thanks,
 
Ben
 
Entering permissions and ttyUSB0 into Googel brought met to #chmod a+rw /dev/ttyUSB0
 
It works now ! 
Just do some reading if there are not to much rights given away.
 
Thanks a BIG lot !!

---

### Post by jamesisin on 2010-05-22
You should NOT change permissions inside /dev.

Where gmargo was talking about is within user settings:

System --> Administration --> Users and Groups

Though you should already have the correct permissions if this is the only account you built on your new machine.

Also, I do not recommend running the command line as root.  It is much preferred to use sudo to provide elevated privileges.

---

### Post by gmargo on 2010-05-22
You should not change /dev/ permissions that way.  It will probably not last across a reboot.  There is a proper way; I think you have to edit udev rules.

I wanted to see the original permissions on the device.  I don't have a USB device to show so I'll use ttyS0, but what I expect to see is something like this:
```

$ ls -l /dev/ttyS0
crw-rw---- 1 root dialout 4, 64 May 22 09:02 /dev/ttyS0

```If you run your rigctl script as root, it works since the device is rw to root.  If you run it as a normal user, it will probably work, since a normal user is generally a member of the "dialout" group. (Run "id" to see all the groups you belong to.)  The web server "lighttpd" runs under the userid "www-data" and only belongs to the "www-data" group.  Hence the CGI script, running under lighttpd, runs as "www-data" and hence does not have permission to access the device.

You should check /var/log/lighttpd/error.log, which will probably contain the error messages from rigctl.

---

### Post by jamesisin on 2010-05-22
gmargo - Wouldn't he just have to change permissions on the mount point?

---

### Post by gmargo on 2010-05-22
> **jamesisin said:**
> gmargo - Wouldn't he just have to change permissions on the mount point?
What mount point are you talking about?  /dev?

After reading /lib/udev/rules.d/README and /etc/udev/rules.d/README, I think the proper method of changing the device permission is to create a file named **/etc/udev/rules.d/rig.rules** with the following content:
```

KERNEL=="ttyUSB0", GROUP="dialout", MODE="666"

```Untested, corrections welcome.  (Or something similar; we still don't know the original permissions.)

---

### Post by jamesisin on 2010-05-22
That sounds better.  I was thinking of the USB device as a drive (in which case it would have a mount point somewhere/when).

---

### Post by benzan on 2010-05-22
> **gmargo said:**
> What mount point are you talking about? /dev?
 
After reading /lib/udev/rules.d/README and /etc/udev/rules.d/README, I think the proper method of changing the device permission is to create a file named **/etc/udev/rules.d/rig.rules** with the following content:
```

KERNEL=="ttyUSB0", GROUP="dialout", MODE="666"

```Untested, corrections welcome. (Or something similar; we still don't know the original permissions.)
 
The original permissions are: 
 
crw-rw---- 1 root dialout 188, 0 2010-05-22 17:51 ttyUSB0
 
I will set them back to the original permissions and try your solutions as described above.
 
Thanks for your response, to all !
 
Regards,
Ben

---

### Post by benzan on 2010-05-22
> **gmargo said:**
> What mount point are you talking about?  /dev?

After reading /lib/udev/rules.d/README and /etc/udev/rules.d/README, I think the proper method of changing the device permission is to create a file named **/etc/udev/rules.d/rig.rules** with the following content:
```

KERNEL=="ttyUSB0", GROUP="dialout", MODE="666"

```Untested, corrections welcome.  (Or something similar; we still don't know the original permissions.)

Tested, no corrections needed, I did create the file as described, rebooted the system, started the system as normal user, run the script from another (Windows)PC, and all works the way I wanted.

Frequency can be changed and is displayed when requested.

Big thanks again !!

Ben

---

