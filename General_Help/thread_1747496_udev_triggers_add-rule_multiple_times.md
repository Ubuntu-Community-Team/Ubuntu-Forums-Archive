---
title: "udev triggers add-rule multiple times"
date: 2011-05-02
forum: General Help
---

### Post by mark46 on 2011-05-02
On Ubuntu 10.04 I would like to setup udev to execute a  backup script when a specific USB drive is inserted. Udev detects the USB drive, but my script is executed 7 times instead of just once. Can't figure out what's wrong... any suggestions?

My udev rules file:
```

/etc/udev/rules.d# cat 20-stick.rules 
ACTION=="add", ATTRS{vendor}=="Kingston", ATTRS{model}=="DataTraveler G2 ", RUN="/usr/local/bin/sync.sh"

```Dummy backup script: connecting USB drive results in 7 times date written to /tmp/test
```

/usr/local/bin# cat sync.sh
#! /bin/sh

if [ "$ACTION" = "add" ]; then
  date >> /tmp/test
fi

```According to "udevadm info" there is only one device that meets the conditions of the udev rule:
```

...
# udevadm info --attribute-walk --name /dev/sdc1
 looking at parent device '/devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host6/target6:0:0/6:0:0:0':
    KERNELS=="6:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="3"
    ATTRS{vendor}=="Kingston"
    ATTRS{model}=="DataTraveler G2 "
    ATTRS{rev}=="1.00"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x179"
    ATTRS{iodone_cnt}=="0x179"
    ATTRS{ioerr_cnt}=="0x2"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{dh_state}=="detached"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"
    ATTRS{max_sectors}=="240"
...

```But "udevadm monitor" shows multiple add events. How to guarantee only one add-event triggers my script?
```

# udevadm monitor --udev
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing

UDEV  [1304372807.804734] remove   /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host4/target4:0:0/4:0:0:0/scsi_generic/sg3 (scsi_generic)
UDEV  [1304372807.807433] remove   /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host4/target4:0:0/4:0:0:0/bsg/4:0:0:0 (bsg)
UDEV  [1304372807.810878] remove   /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host4/target4:0:0/4:0:0:0/scsi_disk/4:0:0:0 (scsi_disk)
UDEV  [1304372807.811714] remove   /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host4/target4:0:0/4:0:0:0/scsi_device/4:0:0:0 (scsi_device)
UDEV  [1304372807.813600] remove   /devices/virtual/bdi/8:32 (bdi)
UDEV  [1304372807.827343] remove   /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host4/target4:0:0/4:0:0:0/block/sdc (block)
UDEV  [1304372807.832893] remove   /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host4/target4:0:0/4:0:0:0 (scsi)
UDEV  [1304372807.835255] remove   /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host4/target4:0:0 (scsi)
UDEV  [1304372807.859607] remove   /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host4/scsi_host/host4 (scsi_host)
UDEV  [1304372807.862542] remove   /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host4 (scsi)
UDEV  [1304372807.862606] remove   /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0 (usb)
UDEV  [1304372807.863270] remove   /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1 (usb)
UDEV  [1304372809.042488] add      /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1 (usb)
UDEV  [1304372809.048655] add      /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0 (usb)
UDEV  [1304372809.056032] add      /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host5 (scsi)
UDEV  [1304372809.059443] add      /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host5/scsi_host/host5 (scsi_host)
UDEV  [1304372814.073370] add      /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host5/target5:0:0 (scsi)
UDEV  [1304372814.095754] add      /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host5/target5:0:0/5:0:0:0 (scsi)
UDEV  [1304372814.141571] add      /devices/virtual/bdi/8:32 (bdi)
UDEV  [1304372814.157331] add      /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host5/target5:0:0/5:0:0:0/scsi_device/5:0:0:0 (scsi_device)
UDEV  [1304372814.163050] add      /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host5/target5:0:0/5:0:0:0/bsg/5:0:0:0 (bsg)
UDEV  [1304372814.170456] add      /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host5/target5:0:0/5:0:0:0/scsi_disk/5:0:0:0 (scsi_disk)
UDEV  [1304372814.178962] add      /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host5/target5:0:0/5:0:0:0/scsi_generic/sg3 (scsi_generic)
UDEV  [1304372814.181886] change   /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host5/target5:0:0/5:0:0:0 (scsi)
UDEV  [1304372814.429233] add      /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host5/target5:0:0/5:0:0:0/block/sdc (block)
UDEV  [1304372814.729185] add      /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host5/target5:0:0/5:0:0:0/block/sdc/sdc1 (block)
UDEV  [1304372815.040884] change   /devices/pci0000:00/0000:00:11.2/usb1/1-2/1-2.1/1-2.1:1.0/host5/target5:0:0/5:0:0:0/block/sdc (block)

```

---

### Post by mark46 on 2011-05-08
Solved by making the udev-rule more specific by matching for SUBSYSTEM. Now the script is indeed executed just once.

```

/etc/udev/rules.d# cat 20-stick.rules
ACTION=="add", SUBSYSTEM=="scsi", ATTRS{vendor}=="Kingston", ATTRS{model}=="DataTraveler G2 ", RUN="/usr/local/bin/sync.sh"

```I guess SUBSYSTEM refers to the string that's output in parentheses by "udevadm monitor".

---

### Post by Vicrem on 2011-06-15
if you put KERNEL=="sd?1" before "ACTION=="add" I belive it will work ;)

---

