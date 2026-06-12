---
title: "Synaptic - Cannot Remove Bluez"
date: 2011-10-09
forum: General Help
---

### Post by Quarkrad on 2011-10-09
Running 10.10.  I had to do some testing to get a bluetooth keyboard/mouse working - I had to install **blueman** and **bluez** via the software centre. I have finished the test and tried to remove both packages via Synaptic.  I have removed blueman but cannot remove bluez - I get the message:

E: /var/cache/apt/archives/bluez_4.89-0ubuntu1~maverick_amd64.deb: subprocess new pre-removal script returned error exit status 1


I have tried upgrading it (to then remove it) but I get the same error.

Any help appreciated to remove bluez.

---

### Post by jonkiribati on 2011-10-09
did you try using dpkg command ? dpkg -r package

---

### Post by raja.genupula on 2011-10-09
+1
Do this uninstall

```
sudo apt-get --purge remove bluez
```
that will delete all of bluez files.

Let me know what you got

---

### Post by Quarkrad on 2011-10-10
This is the output:

[B]dad@dadubuntu:~$ sudo apt-get --purge remove bluez
[sudo] password for dad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  obex-data-server libbluetooth3
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  bluez*
0 upgraded, 0 newly installed, 1 to remove and 20 not upgraded.
After this operation, 1,397kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 211634 files and directories currently installed.)
Removing bluez ...
Can't get device info: No such device
invoke-rc.d: initscript bluetooth, action "stop" failed.
dpkg: error processing bluez (--purge):
 subprocess installed pre-removal script returned error exit status 1
postinst called with unknown argument `abort-remove'
Errors were encountered while processing:
 bluez
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]

I haven't got the bluetooth usb dongle in the machine - do you think it should be plugged in to remove the software?

---

### Post by raja.genupula on 2011-10-10
I am not sure about this but please give a try.
open your gnome system monitor and then at process tab look for Bluetooth process and kill it .then again try to remove bluez.

---

### Post by Quarkrad on 2011-10-10
Afraid there are no such processes running.

---

### Post by raja.genupula on 2011-10-11
while doing uninstalling open any one , software center ,synaptic or terminal.Do the removing from opening anyone and close the remaining.

one more thing that can help us 

Go into /var/lib/dpkg/info and delete everything that had the name of the program giving you errors......

and try again .

let me know what you got.

All the best.

---

### Post by Quarkrad on 2011-10-12
That did it - thank you very much for your help.

---

### Post by raja.genupula on 2011-10-12
I am glad that your issue solved.You're welcome.
Enjoy Ubuntu.

---

