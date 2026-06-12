---
title: "Udev's ID_BUS property for usb drives/partitions"
date: 2012-03-08
forum: General Help
---

### Post by j_kubik on 2012-03-08
On my old computer I used kubunutu 10.04 32bit, and for automatic mounting of usb devices i used self-written script called from udev:

```
#!/bin/bash

#this applies only to the mounts that are not defined in fstab
MOUNT_BASE=/mnt

# Takes path of directory, and returns not-mounted path to possibly not existing,
# but possible to be created directory
function get_unmounted_dir {
    i=1;
    name="$1";

    while [ -n "`mount | cut -d " " -f3 | grep "^$name$"`" ] || ( [ -e "$name" ] && [ ! -d "$name" ] )
    do
        name="$1$i"
        i=$(($i+1))
    done

    echo "$name";
}

echo "Attemptting to mount" > /tmp/mountlog

# Some test of what actually we are doing currently
if  [ "x$SUBSYSTEM" != "xblock" ]
then
   echo "Not using block subsystem" >> /tmp/mountlog
   exit 0;
fi

case "x$DEVTYPE" in
"xpartition")
  if [ "x$ID_BUS" != "xusb" ]
  then
    echo "Partition, but not on usb: it's on $ID_BUS" >> /tmp/mountlog
    exit 0
  fi
;;
"xdisk")
  if [ "x$ID_BUS" != "xata" ]
  then
    echo "Disk, but not on ata" >> /tmp/mountlog
    exit 0
  fi

  blockdev --getsz $DEVNAME
  if [ $? -ne 0 ]
  then
    echo "Disk, but empty - probably removed" >> /tmp/mountlog
    exit 0;
  fi
;;
*)
  echo "Unknown devtype: $DEVTYPE" >> /tmp/mountlog
  exit 0
;;
esac

echo "Trying to mount" >> /tmp/mountlog

# Get the list of mountable devices
mountables=`grep -ve "^#" /etc/fstab | cut -d " " -f1`;

# Compare mountable list with given device and its uuid
if [ -n "`echo "$mountables" | grep -e "^$DEVNAME$"`" ] || [ -n "`echo "$mountables" | grep -e "^UUID=$ID_FS_UUID$"`" ]
then
    # mount if fstab shows how to
    echo "Trying to mount $DEVNAME using fstab information." >> /tmp/mountlog
    mount $DEVNAME
    echo "Mount returned with code $?, ant current status is:" >> /tmp/mountlog
    mount >> /tmp/mountlog
else

    # if we have label given then use label as mount directory, if not, then use device name
    if [ -n "$ID_FS_LABEL" ]
    then
        mnt_point="$MOUNT_BASE/$ID_FS_LABEL";
    else
        mnt_point="$MOUNT_BASE/`basename $DEVNAME`";
    fi

    mnt_point="`get_unmounted_dir "$mnt_point"`";

    
    if [ ! -e "$mnt_point" ]
    then
        mkdir "$mnt_point";
    fi

    mount $DEVNAME $mnt_point;

fi
```

It is being started by udev rules:

```
ACTION=="add" SUBSYSTEM=="block" ENV{DEVTYPE}=="partition" RUN+="/usr/script/udevmount"
ACTION=="remove" SUBSYSTEM=="block" ENV{DEVTYPE}=="partition" RUN+="/usr/script/udevumount"
```


However after transfering the script to new computer with kubuntu 10.10 x64, the script stopped working. I know that it's being called because of logging done to tmp, but it appears that ID_BUS property for usb partitions instead of "usb" is "ata". Is this a bug in udev, or is system someghow smartly mapping usb into ata in the background so that udev is at least theoretically correct?

---

