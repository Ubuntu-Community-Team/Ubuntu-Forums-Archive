---
title: "UDEV check ATTRS"
date: 2012-06-13
forum: General Help
---

### Post by corest on 2012-06-13
Description of problem. There are four photocameras. Two of them - Sony and another two -  Canon. It does not matter what models. Important is that the canon in the system is determined as a camera (for exchange by ptp), and sony - as a flash-drive. System - Ubuntu 12.04. In /etc/udev/rules.d/ i've create 99-cams.rules. Now there is no access to script, so i'l write it's structure:

KERNEL == "block", GOTO "label1"
KERNEL! = "Block", GOTO "label2"

LABEL = "label1"
# Actions with  Sony
LABEL = "label2"
# Actions with Canon.

That's works fine. What I need? i need to check idVendor and idProduct. I wrote this:

KERNEL == "block", ATTRS{idVendor}== "xx", ATTRS{idProduct}=="yy", GOTO "label1"
KERNEL! = "Block", ATTRS{idVendor}=="zz", ATTRS{idProduct}=="qq", GOTO "label2"

LABEL = "label1"
# Actions with photocamera with xx idVendor and yy idProduct
LABEL = "label2"
# Actions with photocamera with zz idVendor and qq idProduct


The problem - ATTRS just igrnoring. I can write anything in ATTRS and udev rule will works as defined in first example. Already tried to change ATTRS to ATTR and SYSFS - nothing changes. Maybe ubuntu 12.04 has some new rules syntax?

---

### Post by matt_symes on 2012-06-13
Hi

Have you used

```
udevadm
```

on the device node to check that combination of KERNEL and ATTRS{..} are valid for the cameras ?

Plug a camera in. Take a note of the device file created for it in /dev.

Open a terminal and type

```
udevadm info --attribute-walk --name=/dev/<device_file>
```

Pick out attributes that can uniquely identify the device.

You can use both ATTR and ATTRS. The difference between them is that ATTRS will look up the hierarchy for the device whereas ATTR will not.

From ```
man udev
```

> ATTR{filename}
           Match sysfs attribute values of the event device. Trailing whitespace in the attribute values is ignored unless the specified match value itself contains
           trailing whitespace.

 > ATTRS{filename}
           Search the devpath upwards for a device with matching sysfs attribute values. If multiple ATTRS matches are specified, all of them must match on the same
           device. Trailing whitespace in the attribute values is ignored unless the specified match value itself contains trailing whitespace.

Kind regards

---

### Post by corest on 2012-06-14
i've read attrs with udevadm and get 


  looking at device '/devices/pci0000:00/0000:00:1d.7/usb1/1-6':
    KERNEL=="1-6"
    SUBSYSTEM=="usb"
    DRIVER=="usb"
    ATTR{configuration}==""
    ATTR{bNumInterfaces}==" 1"
    ATTR{bConfigurationValue}=="1"
    ATTR{bmAttributes}=="c0"
    ATTR{bMaxPower}=="  0mA"
    ATTR{urbnum}=="601"
    ATTR{idVendor}=="054c"
    ATTR{idProduct}=="0295"
    ATTR{bcdDevice}=="0100"
    ATTR{bDeviceClass}=="00"
    ATTR{bDeviceSubClass}=="00"
    ATTR{bDeviceProtocol}=="00"
    ATTR{bNumConfigurations}=="1"
    ATTR{bMaxPacketSize0}=="64"
    ATTR{speed}=="480"
    ATTR{busnum}=="1"
    ATTR{devnum}=="54"
    ATTR{devpath}=="6"
    ATTR{version}==" 2.00"
    ATTR{maxchild}=="0"
    ATTR{quirks}=="0x0"
    ATTR{avoid_reset_quirk}=="0"
    ATTR{authorized}=="1"
    ATTR{manufacturer}=="Sony"
    ATTR{product}=="DSC-W180"
    ATTR{serial}=="d5b57061806e"

so i write udev rule with that idVendor and idProduct. But i have  another problem. I run script when detect usb device, but i need mount sd-card from camera before. It's my udev:


# Start at sdb to avoid system harddrive.
#KERNEL=="sd[b-z][0-9]", ATTR{idVendor}=="054c", ATTR{idProduct}=="033e", GOTO="camera_card"
#KERNEL=="1-6|sd[b-z][0-9]",
#04b0:0186
#054c 033e
ATTR{idVendor}=="054c", ATTR{idProduct}=="0295", GOTO="camera_card"
GOTO="UNKNOW"

LABEL="camera_card"

# Import FS infos
IMPORT{program}="/sbin/blkid -o udev -p %N"

# Get a label if present, otherwise specify one
ENV{ID_FS_LABEL}!="", ENV{dir_name}="%E{ID_FS_LABEL}"
ENV{ID_FS_LABEL}=="", ENV{dir_name}="usbhd-%k"

# Global mount options
ACTION=="add", ENV{mount_options}="defaults,relatime"
# Filesystem-specific mount options
ACTION=="add", ENV{ID_FS_TYPE}=="vfat|ntfs", ENV{mount_options}="$env{mount_options},utf8,gid=100,umask=002"

# Mount the device
ACTION=="add", RUN+="/bin/mkdir -p /media/%E{dir_name}", RUN+="/bin/mount -o $env{mount_options} /dev/%k /media/%E{dir_name}", RUN+="/opt/cam.sh"

# Clean up after removal
ACTION=="remove", ENV{dir_name}!="", RUN+="/bin/umount -l /media/%E{dir_name}", RUN+="/bin/rmdir /media/%E{dir_name}"

GOTO="media_by_label_auto_mount_end"

LABEL="UNKNOW"
#ACTION=="add", RUN+="/opt/cam.sh"

# Exit
LABEL="media_by_label_auto_mount_end"

and /opt/cam.sh:

#!/bin/sh
#location=/mnt/share
location=/home/tech
dest=photo_$(date +%Y-%m-%d-%H:%M:%S)

set -x
xhost local:tech
export DISPLAY=:0.0

su tech -c 'gphoto2 --auto-detect && mkdir '$location/$dest' && cd '$location/$dest' && xterm -geometry 158x54+0+0 -e "gphoto2 --get-all-files -R && echo "blabla!!!" && sleep 20"'

But script runs before mounting device, so gphoto2 can't read photos. Any ideas please?

---

### Post by matt_symes on 2012-06-14
Hi

Try Amalgamating the RUN commands in to one comma separated run command. I don't know if it will work but try it. 

It's possible that multiple RUN commands are run concurrently.

```
# Start at sdb to avoid system harddrive.
#04b0:0186
#054c 033e
ATTR{idVendor}=="054c", ATTR{idProduct}=="0295", GOTO="camera_card"
GOTO="media_by_label_auto_mount_end"

LABEL="camera_card"

# Import FS infos
IMPORT{program}="/sbin/blkid -o udev -p %N"

# Get a label if present, otherwise specify one
ENV{ID_FS_LABEL}!="", ENV{dir_name}="%E{ID_FS_LABEL}"
ENV{ID_FS_LABEL}=="", ENV{dir_name}="usbhd-%k"

# Global mount options
ACTION=="add", ENV{mount_options}="defaults,relatime"
# Filesystem-specific mount options
ACTION=="add", ENV{ID_FS_TYPE}=="vfat|ntfs", ENV{mount_options}="$env{mount_options},utf8,gid=1 00,umask=002"

# Mount the device
ACTION=="add", **RUN+="/bin/mkdir -p /media/%E{dir_name}; /bin/mount -o $env{mount_options} /dev/%k /media/%E{dir_name}; /opt/cam.sh"**

# Clean up after removal
ACTION=="remove", ENV{dir_name}!="", **RUN+="/bin/umount -l /media/%E{dir_name}; /bin/rmdir /media/%E{dir_name}"**

# Exit
LABEL="media_by_label_auto_mount_end"
```

Kind regards

---

