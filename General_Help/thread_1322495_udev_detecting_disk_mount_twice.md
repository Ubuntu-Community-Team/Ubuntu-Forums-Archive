---
title: "udev detecting disk mount twice"
date: 2009-11-11
forum: General Help
---

### Post by EnlistedSquire on 2009-11-11
Hi,

I've set up a udev rule that detects when I've connected my digital video camera and runs a script that will copy all the movies from it to my server automatically.

The script runs fine when run from a terminal but I think the problem is that because the camera switches into data transfer mode when connected udev detects it being connected (at least) twice. This causes it to execute my script twice and causes it to go haywire (System Monitor shows about ten "cp" processes instead of just the one).

Here's the output of udevmonitor when I connect it:

```
UEVENT[1257917859.979307] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2
UDEV  [1257917859.979307] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2
UEVENT[1257917859.982192] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0
UDEV  [1257917859.990191] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0
UEVENT[1257917859.997491] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33
UEVENT[1257917859.998181] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/scsi_host/host33
UEVENT[1257917860.003148] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/usb_endpoint/usbdev1.33_ep81
UEVENT[1257917860.003922] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/usb_endpoint/usbdev1.33_ep02
UEVENT[1257917860.004979] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/usb_device/usbdev1.33
UEVENT[1257917860.005798] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/usb_endpoint/usbdev1.33_ep00
UDEV  [1257917860.040937] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/usb_endpoint/usbdev1.33_ep00
UDEV  [1257917860.113709] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/usb_device/usbdev1.33
UDEV  [1257917860.190578] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33
UDEV  [1257917860.205920] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/usb_endpoint/usbdev1.33_ep81
UDEV  [1257917860.221561] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/usb_endpoint/usbdev1.33_ep02
UDEV  [1257917860.238642] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/scsi_host/host33
UEVENT[1257917865.024517] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0
UDEV  [1257917865.024517] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0
UEVENT[1257917865.025994] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0
UEVENT[1257917865.026944] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0/scsi_disk/33:0:0:0
UDEV  [1257917865.079711] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0
UEVENT[1257917865.096513] change@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0
UEVENT[1257917865.153752] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0/block/sdb
UEVENT[1257917865.154462] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0**/block/sdb/sdb1**
UEVENT[1257917865.154765] add@/devices/virtual/bdi/8:16
UEVENT[1257917865.154867] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0/scsi_device/33:0:0:0
UEVENT[1257917865.154974] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0/scsi_generic/sg1
UDEV  [1257917865.164108] add@/devices/virtual/bdi/8:16
UEVENT[1257917865.177166] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:1
UEVENT[1257917865.177327] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:1/scsi_disk/33:0:0:1
UEVENT[1257917865.230388] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:1/block/sdc
UEVENT[1257917865.231090] add@/devices/virtual/bdi/8:32
UEVENT[1257917865.232020] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:1/scsi_device/33:0:0:1
UEVENT[1257917865.232886] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:1/scsi_generic/sg2
UDEV  [1257917865.240608] add@/devices/virtual/bdi/8:32
UDEV  [1257917865.249720] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:1
UDEV  [1257917865.448659] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0/scsi_disk/33:0:0:0
UDEV  [1257917865.801749] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0/scsi_device/33:0:0:0
UDEV  [1257917865.820297] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:1/scsi_disk/33:0:0:1
UDEV  [1257917865.833700] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0/scsi_generic/sg1
UDEV  [1257917865.942622] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:1/scsi_device/33:0:0:1
UDEV  [1257917866.025806] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:1/scsi_generic/sg2
UDEV  [1257917866.524589] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0/block/sdb
UDEV  [1257917866.577681] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:1/block/sdc
UDEV  [1257917866.582932] change@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0
UDEV  [1257917866.942703] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0/block**/sdb/sdb1**
```

sdb1 is detected twice.

Is there a way to fix this, or failing that is there a line I can put in the bash script to make it detect if it's already running? I'm by no means an expert on scripting, this is a very simply script.

Here it is:

```
#!/bin/bash
#DATE=`date +%y%m%d%H%M`
#mkdir /home/storage/temp/files_$DATE
#mount /dev/sdb1 /home/storage/extern/GZ-MG40-1
#sleep 5
#cp -r /home/storage/extern/GZ-MG40-1/* /home/storage/temp/files_$DATE
#sleep 5
#umount /home/storage/extern/GZ-MG40-1
```

Thanks.

---

### Post by mr_steve on 2009-11-11
> **EnlistedSquire said:**
> Hi,

I've set up a udev rule that detects when I've connected my digital video camera and runs a script that will copy all the movies from it to my server automatically.

The script runs fine when run from a terminal but I think the problem is that because the camera switches into data transfer mode when connected udev detects it being connected (at least) twice. This causes it to execute my script twice and causes it to go haywire (System Monitor shows about ten "cp" processes instead of just the one).

Here's the output of udevmonitor when I connect it:

```
UEVENT[1257917859.979307] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2
UDEV  [1257917859.979307] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2
UEVENT[1257917859.982192] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0
UDEV  [1257917859.990191] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0
UEVENT[1257917859.997491] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33
UEVENT[1257917859.998181] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/scsi_host/host33
UEVENT[1257917860.003148] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/usb_endpoint/usbdev1.33_ep81
UEVENT[1257917860.003922] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/usb_endpoint/usbdev1.33_ep02
UEVENT[1257917860.004979] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/usb_device/usbdev1.33
UEVENT[1257917860.005798] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/usb_endpoint/usbdev1.33_ep00
UDEV  [1257917860.040937] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/usb_endpoint/usbdev1.33_ep00
UDEV  [1257917860.113709] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/usb_device/usbdev1.33
UDEV  [1257917860.190578] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33
UDEV  [1257917860.205920] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/usb_endpoint/usbdev1.33_ep81
UDEV  [1257917860.221561] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/usb_endpoint/usbdev1.33_ep02
UDEV  [1257917860.238642] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/scsi_host/host33
UEVENT[1257917865.024517] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0
UDEV  [1257917865.024517] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0
UEVENT[1257917865.025994] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0
UEVENT[1257917865.026944] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0/scsi_disk/33:0:0:0
UDEV  [1257917865.079711] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0
UEVENT[1257917865.096513] change@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0
UEVENT[1257917865.153752] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0/block/sdb
UEVENT[1257917865.154462] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0**/block/sdb/sdb1**
UEVENT[1257917865.154765] add@/devices/virtual/bdi/8:16
UEVENT[1257917865.154867] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0/scsi_device/33:0:0:0
UEVENT[1257917865.154974] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0/scsi_generic/sg1
UDEV  [1257917865.164108] add@/devices/virtual/bdi/8:16
UEVENT[1257917865.177166] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:1
UEVENT[1257917865.177327] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:1/scsi_disk/33:0:0:1
UEVENT[1257917865.230388] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:1/block/sdc
UEVENT[1257917865.231090] add@/devices/virtual/bdi/8:32
UEVENT[1257917865.232020] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:1/scsi_device/33:0:0:1
UEVENT[1257917865.232886] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:1/scsi_generic/sg2
UDEV  [1257917865.240608] add@/devices/virtual/bdi/8:32
UDEV  [1257917865.249720] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:1
UDEV  [1257917865.448659] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0/scsi_disk/33:0:0:0
UDEV  [1257917865.801749] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0/scsi_device/33:0:0:0
UDEV  [1257917865.820297] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:1/scsi_disk/33:0:0:1
UDEV  [1257917865.833700] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0/scsi_generic/sg1
UDEV  [1257917865.942622] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:1/scsi_device/33:0:0:1
UDEV  [1257917866.025806] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:1/scsi_generic/sg2
UDEV  [1257917866.524589] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0/block/sdb
UDEV  [1257917866.577681] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:1/block/sdc
UDEV  [1257917866.582932] change@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0
UDEV  [1257917866.942703] add@/devices/platform/fsl-ehci.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/host33/target33:0:0/33:0:0:0/block**/sdb/sdb1**
```sdb1 is detected twice.

Is there a way to fix this, or failing that is there a line I can put in the bash script to make it detect if it's already running? I'm by no means an expert on scripting, this is a very simply script.

Here it is:

```
#!/bin/bash
#DATE=`date +%y%m%d%H%M`
#mkdir /home/storage/temp/files_$DATE
#mount /dev/sdb1 /home/storage/extern/GZ-MG40-1
#sleep 5
#cp -r /home/storage/extern/GZ-MG40-1/* /home/storage/temp/files_$DATE
#sleep 5
#umount /home/storage/extern/GZ-MG40-1
```Thanks.

I also am absolutely not a BASH expert, but here's the general idea I would use:

At the start of the script, check to see if a file, e.g. "/tmp/photocopyscript.lock" exists.
If it does, die.
If it doesn't, create it, e.g. "touch /tmp/photocopyscript.lock" and then run through the script.
At the end of the script, rm /tmp/photocopyscript.lock.

Make sense?

The other, and probably better, solution, would be to figure out what's going on with your UDEV rules and fix it, but that's another area I'm not too sharp at.

---

### Post by EnlistedSquire on 2009-11-11
Thanks. I had a similar idea but no idea how I'd code that. I'm at work now but I'll have a bit of a Google when I get home if I've had no other replies by then.

I think the udev thing is to do with the camera:

1. I connect the camera and udev detects this.
2. The camera detects it's been connected to a PC and switches to data transfer mode.
3. udev detects this as a another device being connected.

Cheers.

---

### Post by EnlistedSquire on 2009-11-11
OK, here's my new script:

```
#!/bin/bash
DATE=`date +%y%m%d%H%M%S`
LOG=/home/storage/temp/$DATE.log
if [ -e /home/storage/temp/.lock ]
then
echo ".lock exists, quitting" > $LOG
exit 1;
fi
echo ".lock doesn't exist, running" > $LOG
touch /home/storage/temp/.lock
mkdir /home/storage/temp/files_$DATE
mount /dev/sdb1 /home/storage/extern/GZ-MG40-1
sleep 5
cp -r /home/storage/extern/GZ-MG40-1/* /home/storage/temp/files_$DATE
sleep 5
umount /home/storage/extern/GZ-MG40-1
rm /home/storage/temp/.lock
```

If I run this from a terminal it works beautifully. If there's no .lock file the copy runs, if I create a file called .lock and then run the script it quits without doing anything.

Letting it get launched by udev is a different story however.

As you can see, I've made the script create log files with what it's doing so I can see how many times it's tried to run.

When I connect the camera, the directory files_$DATE is created but remains empty. I get two log files, one with the same time as the directory and one a second older but both contain the text ".lock exists, quitting".

So the behaviour of the second attempt to run it makes sense - no directory is created and this fact is logged. But the first time doesn't make any sense to me. This is what I assume is happening - the script decides there's no .lock file and logs this fact. Creates the .lock file and the directory, then decides there is a .lock file and it should quit. At this moment the original log file is overwritten with a new one saying it's quitting.

Can anyone advise?

For good measure, here's my udev rule:

```
SUBSYSTEMS=="scsi", ATTRS{vendor}=="JVC     ", ATTRS{model}=="GZ-MG40         ", ATTRS{rev}=="1.1 ", RUN+="/usr/local/bin/fork /usr/local/bin/getmovs"
```

/usr/local/bin/getmovs is my script as above and /usr/local/bin/fork is a piece of code I found to detach the script from udev. This is the contents but I've tried it with or without this script and got the same results:

```
#!/bin/sh
/usr/bin/nohup $@ 1>/dev/null 2>&1 </dev/null &
```

Thanks.

---

### Post by EnlistedSquire on 2009-11-12
I finally got it all working properly and learned a hell of a lot of bash in the process.

Here's the code that is working:

```
#!/bin/bash
DATE=`date +%y%m%d%H%M%S`
LOCKFILE=/home/storage/temp/.lockfile
LOG=/home/storage/temp/$DATE"_"$$.log
echo "`date +%s` pid=$$" >> $LOG
echo "`date +%s` running" >> $LOG
if [ ! -e $LOCKFILE ];
echo "`date +%s` making lockfile" >> $LOG
( set -o noclobber; echo "$$" > "$LOCKFILE") 2> /dev/null; 
then
   trap 'rm -f "$LOCKFILE"; umount /home/storage/extern/GZ-MG40-1/; echo "`date +%s` process killed" >> $LOG; exit $?' INT TERM EXIT
sleep 5
echo "`date +%s` making temp dir" >> $LOG
mkdir /home/storage/temp/files_$DATE"_"$$
#sleep 20
echo "`date +%s` mounting drive" >> $LOG
mount /dev/sdb1 /home/storage/extern/GZ-MG40-1
echo "`date +%s` copying files" >> $LOG
cp -r /home/storage/extern/GZ-MG40-1/* /home/storage/temp/files_$DATE"_"$$
sleep 5
echo "`date +%s` dismounting drive" >> $LOG
umount /home/storage/extern/GZ-MG40-1
   rm -f "$LOCKFILE"
   trap - INT TERM EXIT
else
echo "`date +%s` lock exists, exiting" >> $LOG
exit;
fi
echo "`date +%s` exiting, got to the end." >> $LOG
exit;
```

I've just got to go through and remove all the logging that I put in for debugging purposes.

Scary thing: by creating a logfile with the pid in the file name I was able to see how many times the script was launched each time I plugged in the camera. The answer is 13. What's going on there I've no idea. Fortunately, with this script I've managed to get twelve of them to bomb out. Phew!

---

### Post by Michael Meuli on 2010-10-26
Thanks to you I can now plug in my Nikon D90 camera and the pictures and films are automatically copied to my computer, renamed and sorted. Somehow my script called by udev was executed twice. No idea why.

To me it doesn't make sense to set noclobber the way you do it
```
if [ ! -e $LOCKFILE ];
echo "`date +%s` making lockfile" >> $LOG
( set -o noclobber; echo "$$" > "$LOCKFILE") 2> /dev/null; 
then
```
I found a nice explanation about lockfile here:
[HTML]http://www.davidpashley.com/articles/writing-robust-shell-scripts.html[/HTML]
And about noclobber here:
[HTML]http://www.cyberciti.biz/tips/howto-keep-file-safe-from-overwriting.html[/HTML]
And finely replaced these lines by:
```
if ( set -o noclobber; echo $$ > $lockfile) 2> /dev/null
then
```
So here are my udev rules and scripts:
/etc/udev/rules.d/usb-storage-custom.rules:
```
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0421", SYSFS{serial}=="000006532642", RUN+="/usr/local/bin/nikimpstart.sh /usr/local/bin/nikimport.sh"  
```
/usr/local/bin/nikimpstart.sh:
```
#! /bin/bash
/usr/bin/nohup $@ 1>/dev/null 2>&1 </dev/null &
```
/usr/local/bin/nikimport.sh:
```
#!/bin/bash

user=michael
lockfile=/home/$user/.lockfile
export DISPLAY=:0.0

if ( set -o noclobber; echo $$ > $lockfile) 2> /dev/null
then
trap 'rm -f "$lockfile"; exit $?' INT TERM EXIT
su $user -c 'zenity --info --timeout=10 --text "Die Bilder werden auf den Computer kopiert.\nBitte warten..." &'
mkdir -p /home/$user/tmp/Nikon
cd /home/$user/tmp/Nikon/
gphoto2 --get-all-raw-data
exiftool '-FileName<DateTimeOriginal' -d /home/$user/Bilder/%Y/%m/%d/%Y%m%d%H%M%S%%-c.%%e /home/$user/tmp/Nikon/*.jpg
exiftool '-FileName<DateTimeOriginal' -d /home/$user/Bilder/NEF/%Y/%m/%d/%Y%m%d%H%M%S%%-c.%%e /home/$user/tmp/Nikon/*.NEF
exiftool '-FileName<DateTimeOriginal' -d /home/$user/Videos/Filme\ Nikon/%Y%m%d%H%M%S%%-c.%%e /home/$user/tmp/Nikon/*.avi
chown -R $user:$user /home/$user/Bilder
chown -R $user:$user /home/$user/Videos/Filme\ Nikon
chmod -R 777 /home/$user/Bilder
chmod -R 777 /home/$user/Videos/Filme\ Nikon
newfolder=$(find /home/$user/Bilder -mindepth 3 -maxdepth 3 -type d -printf "%TY-%Tm-%Td %TT %p\n" | sort -n -r | head -n 1 | cut -d' ' -f3)
su $user -c "/usr/bin/nautilus $newfolder"
sleep 5
rm -f $lockfile
rmdir /home/$user/tmp/Nikon
rmdir /home/$user/tmp
trap - INT TERM EXIT
fi
exit
```
First time I'm writing something. Hope the formating gets all right. For me as an amateur it took me quite some time to get it working and to find relevant information. Also helpful to see something (zenity and nautilus) was this here:
[HTML]http://ubuntuforums.org/showthread.php?t=994233[/HTML]
and some more...
I actualy didn't manage exiftool (which needs to be installed by the way) to be called as a certain user. I tried:
```
su $user -c 'exiftool "-FileName<DateTimeOriginal" -d /home/$user/Bilder/%Y/%m/%d/%Y%m%d%H%M%S%%-c.%%e /home/$user/tmp/Nikon/*.jpg'
```
I can imagine it doesn't work because of the % stuff in there not beeing expanded because of the single quotes but don't know how to do better.
Also the part with gphoto2 could probably be better.
Cheers!

---

### Post by EnlistedSquire on 2010-10-26
I'm glad the information helped. My own script has evolved a bit since I wrote the last post so I might have changed the noclobber stuff, can't remember. I do know it's now using rsync instead of cp though.

---

