---
title: "Spin down idle SATA Drives"
date: 2010-12-30
forum: General Help
---

### Post by octbit on 2010-12-30
I realize this has been asked many times before, but I'm fairly certain I've read through the majority of those threads and haven't found a working solution yet.

I recently built up a Ubuntu Server 10.10 x64 box for backups, serving up files, and development activities.  The server is running SATA drives in AHCI mode.  Because this is a file server I have quite a few hard drives installed, which are currently a mix of WD 1TB Black and Green drives.  I'm attempting to get my non-boot/data only drives to spin down after 10 minutes.  I've tried the following:

1. Edit hdparm.conf with the following, replacing 'b' with the identifier for each disk:

```
/dev/sdb {
     spindown_time = 120
}
```

This fails, and based on my research I'm pretty sure udev isn't properly running the hdparm configuration anyway.

2.  I've also tried manually setting the spin down time with hdparm as follows (via command line and through rc.local):

```
hdparm -q -S 120 /dev/sdb
```

Which states that it successfully set the spin down timer to 10 minutes, but this also fails as the drive never spins down.

3.  Finally, I just forced it to spin down immediately with:

```
hdparm -y /dev/sdb
```

This worked!  Unfortunately, that approach isn't terribly useful.  The drive stayed spun down for 20 minutes (thus far), so I haven't bothered to run iostat, etc to try and figure out if something is keeping the drives active.  I don't believe there is because one of my drives isn't even mounted currently and it also won't spin down automatically.

Any ideas for other things I can try?

Thanks!

---

### Post by XeonBloomfield on 2010-12-30
You can spin down it automatically on startup by adding your command to autostart.

If you want to get automatically spin downing when disk is not active you need to create script checking if mount folder for partition is available.

---

### Post by octbit on 2010-12-30
> **XeonBloomfield said:**
> If you want to get automatically spin downing when disk is not active **you need to create script checking if mount folder for partition is available.**

I'm interested in this approach, but I'm not sure what you're stating here.  For the drives I'm mounting, I've set up the following in fstab:

```
# Data Drives
/dev/sdb1    /mnt/volume001   ext4    defaults     0        2
/dev/sdc1    /mnt/volume002   ext4    defaults     0        2
/dev/sdd1    /mnt/volume003   ext4    defaults     0        2
/dev/sde1    /mnt/volume004   ext4    defaults     0        2 
```

Are you saying I need to check that these mounted properly before running hdparm?

Thanks!
Mike

---

### Post by XeonBloomfield on 2010-12-30
I'm saying that you need to check if it's available to don't spin down used disk.

I will give you that pseudo code:
```
if[ disk_is_unused ]
then
if[ it_is_enabled ] # to don't spin down it second time
then 
spin_down
set_as_disabled # to don't spin down it second time
fi
fi
else
then
set_as_enabled # disk is used
fi
```

---

### Post by dcstar on 2010-12-31
Old script that may be worth a try:

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

### Post by octbit on 2010-12-31
Thanks guys.  I'll work with this and give it a shot.  I assume this is a known issue with hdparm, hence the work arounds?

Thanks!

---

