---
title: "udev rules not working"
date: 2012-06-08
forum: General Help
---

### Post by ktheking on 2012-06-08
Hello,

I'm writing an udev rule to execute a script upon the insertion of an external usb drive. Purpose is to fire off a script that performs the backup ,and creates sounds and screensaver messages for the user. I'm usually never posting questions ,as I can usually find a fix or workaround myself by reading (i'm an rtfm addept :)),but here I'm stuck.

The platform I'm working with is :
> root@felixubuntu:/etc/udev/rules.d# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04 LTS
Release:        12.04
Codename:       precise

More precisely (lol) , the 64-bit version.

My rule is something like this :
> KERNEL=="1-1.5", SUBSYSTEM=="usb", DRIVER=="usb", ATTR{idVendor}=="152d", ATTR{idProduct}=="2329", RUN+="/usr/local/bin/echotest.sh"

saved in the rule file : /etc/udev/rules.d/100-usbbackup

> -rw-r--r-- 1 root root 133 Jun  8 11:25 /etc/udev/rules.d/100-usbbackup

The problem :
Even after restarting the machine, or restarting udev ( service udev restart ) ,the current testscript defined in the udev rule is still not started. 

Really no idea here , been searching for days now ,tried all different combinations with the info I retrieved from these commands :
> udevadm info --attribute-walk --name=/dev/sdg1 2>&1
> udevadm monitor --env

This is a desperate call on other pair of eyes ,looking at the problem differently ,and who might bring the solution.

OR this just might be a bug with udev and Ubuntu 12.04 ?

Really appreciating feedback on this one lads.

Kind regards,

K

---

### Post by ktheking on 2012-06-12
As a temporar workaround I created my proper udev kind of deamon checking for inserted devices (this one checks every 20sec. if the device with the id  152d:2329 is connected ) :

```

#!/bin/sh

#-------------------------
# backuptousbguarddog.sh
#-------------------------

# Check if drive becomes available then start the backup.

TIMETOCHECK=20
LOOPLOCK=1

#kill any previous script that was running ,except the current one
ps auxww | grep "backuptousbguarddog.sh" | grep -v "$$" | grep -v grep | awk '{print $2}' | xargs kill


while [ $LOOPLOCK -eq 1 ]
 do
 sleep $TIMETOCHECK
 CHECKDRIVECONNECT=`(lsusb | grep -c "152d:2329" | sed 's/ //g')`
 if [ $CHECKDRIVECONNECT -eq 1 ]
  then
  echo "---------------------------------------------------------"
  echo "`date +'%Y%m%d%H%M%S'` : Drive connected ,starting backup"
  echo "---------------------------------------------------------"
  /usr/local/bin/dobackup.sh
 fi
 done

```

Then run the script in the background ./backuptousbguarddog.sh &

---

