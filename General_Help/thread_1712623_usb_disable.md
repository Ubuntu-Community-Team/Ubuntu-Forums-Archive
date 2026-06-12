---
title: "usb disable"
date: 2011-03-23
forum: General Help
---

### Post by Rakeshvijayan on 2011-03-23
Dear friends,

  I  am using Ubuntu 10.04 LTS for our desktops user. For the data  security, I want to disable the USB ports for mass storage. 

For disabling the usb, i did the follow steps

System -> Administration -> user and groups

user -> advance setting  -> user privileges ->  uncheck - Access external storage devices automatically

But it is not working, when a  user  attach pen drive it automatically mounting.

i am using  usb  keyboard and mouse. so don't want to disable complete usb port.  i just  want to disable  only the usb mass storage .

---

### Post by sj1410 on 2011-03-23
The USB storage drive automatically detects USB flash or hard drives. You can easily force and disable USB storage devices. The modprobe program used for automatic kernel module loading and can be configured to not load the USB storage driver upon demand. This will prevent the modprobe program from loading the usb-storage module.

Type the following command:
```

# echo 'install usb-storage : ' >> /etc/modprobe.conf

```

---

### Post by suresh_vandiyur on 2011-03-23
> **sj1410 said:**
> The USB storage drive automatically detects USB flash or hard drives. You can easily force and disable USB storage devices. The modprobe program used for automatic kernel module loading and can be configured to not load the USB storage driver upon demand. This will prevent the modprobe program from loading the usb-storage module.

Type the following command:
```

# echo 'install usb-storage : ' >> /etc/modprobe.conf

```
Once runs above command how to re enable the USB storage devices.

Thank you,

Regards,
Suresh

---

### Post by satish_j on 2011-03-23
> **suresh_vandiyur said:**
> Once runs above command how to re enable the USB storage devices.

Thank you,

Regards,
Suresh

```

gksudo gedit /etc/modprobe.conf

```
remove line *install usb-storage* from file,save and reboot

---

### Post by sj1410 on 2011-03-23
root can use the insmod program to load the module manually

---

### Post by Rakeshvijayan on 2011-03-23
This is the result I got when I execute the command from you...I need to know  more about this topic

---

### Post by sj1410 on 2011-03-23
when you paste the last few characters are going on second line

you better try this as root

---

