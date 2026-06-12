---
title: "Force disk power off ?"
date: 2010-08-10
forum: General Help
---

### Post by go4it on 2010-08-10
Hi all,

I have a Samsung N135 notebook which boots well from USB.
When I travel, I am afraid to damage the disk due to shocks.

When I boot from USB and dismounts the build-in disk are the heads parked away
from the platters ? Is the disk not spinning at all ?

Is there a command to force power off of the disk !


Thanks,

D.

---

### Post by dcstar on 2010-08-11
> **go4it said:**
> Hi all,

I have a Samsung N135 notebook which boots well from USB.
When I travel, I am afraid to damage the disk due to shocks.

When I boot from USB and dismounts the build-in disk are the heads parked away
from the platters ? Is the disk not spinning at all ?

Is there a command to force power off of the disk !


Thanks,

D.

I once used this:

```
#!/bin/bash
#
# Script to spin down external drives after "X" seconds
# Usage: sudo ./scsi-idle 1500 (for 25 minutes + sleepval)
#
# Requires sg3-utils package
#

declare -a DID
declare -a DSTATUS
declare -a DTIME
declare -a DOFF

interval=$1
sleepval=120
buspath=/sys/bus/scsi/devices

while [ true ]; do
thetime=`date +%s`

for scsidev in $( ls --format=across $buspath ); do
   if devenum="$( ls ${buspath}/${scsidev} | grep 'block:' )"; then
      devdir=$buspath/$scsidev/$devenum
      read devsize < ${devdir}/size
      read devremove < ${devdir}/removable

      if [ $devremove -eq 0 ] && [ $devsize -gt 0 ]; then # device is the right type
         read newstat < ${devdir}/stat
         hhit=0; listlen=${#DID[@]}  #; echo $listlen $scsidev

         for ((i=0;i<$listlen;i++)); do
            if [ ${DID[$i]} = $scsidev ]; then
               if [ "${DSTATUS[$i]}" = "$newstat" ]; then
                  if [ $[ ${thetime} - ${DTIME[$i]} ] -ge $interval ] \
                  && [ ${DOFF[$i]} -eq 0 ]; then
                   # sg_start --pc=5 /dev/${devenum:6} # put into sleep mode
                     sg_start --stop /dev/${devenum:6} # alternate method
                     echo stop /dev/${devenum:6}
                     DTIME[$i]=$thetime
                     DOFF[$i]=1
                  fi
               else
                  DSTATUS[$i]=$newstat
                  DTIME[$i]=$thetime
                  DOFF[$i]=0
               fi
               hhit=1; break
            fi
         done
         if [ $hhit -eq 0 ]; then   # add new drive to watch list
            DID[$listlen]=$scsidev
            DSTATUS[$listlen]=$newstat
            DTIME[$listlen]=`date +%s`
            DOFF[$listlen]=0
         fi
      fi
   fi
done
sleep $sleepval
done
```

---

### Post by go4it on 2010-08-13
Thank you David,
I will see how I can use this,
Regards,

Go4it

---

### Post by sdennie on 2010-08-13
If the disk isn't mounted, you could essentially turn the disk off with:

```

sudo hdparm -Y /dev/sda

```

Or just spin it down with:

```

sudo hdparm -y /dev/sda

```

You can check status of the drive with:

```

sudo hdparm -C /dev/sda

```

Though, if you've shut down the disk with -Y, it will take a second to spin back up and I think you'll have to shut it back down by issuing the -Y command again.

(Note: It may be /dev/sdb if you've booted from a USB stick)

---

