---
title: "usb device needs root (sudo) to run."
date: 2011-11-09
forum: General Help
---

### Post by dchurch24 on 2011-11-09
Hi,

I have a Velleman USB experiment board which I use for home automation - recently, I have upgraded my main MythTV box to a Revo. Everything is excellent - the TV is nice and crisp etc..., but I used to use the machine that preceded this as the 'server' for devices in the house via USB relays etc...
Everything has been moved to the new box fine, apart from the Velleman device.

I have downloaded the libraries/source for the K8055 program and this has compiled perfectly.

The problem is that if I simply try to launch the software as myself, then I get 'command not found' error.
If I run as sudo, then the program works as expected.
As this is 'home *automation*' obviously, having to log in as root every time I expect the doorbell to ring, or a lamp going on or off upstairs is not ideal! ;-)

I simply don't know how to get this to run as a normal user, can anyone point me in the right direction please?

---

### Post by kerry_s on 2011-11-09
Sounds like the command is not in path, it should be in, /usr/bin not /bin

---

### Post by dchurch24 on 2011-11-09
Hi, thanks for fast reply!

You assumed correctly, it wasn't in /usr/bin/ (although when I did "make install", I remember seeing the cp command copy it to that path).

I copied it there myself, but alas I get the same response.

```

dave@frontroomrevo:~/Automation/k8005/src$ k8055
Could not open the k8055 (port:0)
Please ensure that the device is correctly connected.
dave@frontroomrevo:~/Automation/k8005/src$ sudo k8055
104;0;0;0;42;0

```

I did this:

```

ls -l /usr/bin/ |grep k8
-rwxr-xr-x 1 root   root      30606 2011-11-09 21:25 k8055

```

To see if it yielded any clues.

I'm not sure that changing the owner/group to my user is a good idea? I have a feeling that it's more to do with the device, than the file permissions on the k8055 program.

---

### Post by lisati on 2011-11-09
Just a thought: when you get the "command not found" error, is your system looking for k8**O**55 with a letter "Oh" instead of k8**0**55 with a number zero?

---

### Post by dchurch24 on 2011-11-09
Thanks, but I press TAB to autocomplete, just to be sure I tried it with the 'O' (instead of zero), but then it's not found either.

---

### Post by dchurch24 on 2011-11-09
well, I changed the group/user, then logged out and back in and it's made no difference. I still have to be root to execute.

I'm baffled.

Although I did find this:

[http://libk8055.sourceforge.net/](http://libk8055.sourceforge.net/)

...but the permissions part seems to be Gentoo based, and most is alien to me.

---

### Post by Jouke74 on 2011-11-09
You should make a UDEV rule that allows all permissions for the specific USB device. Something in the trend like 

KERNEL=="hiddev*", MODE="0666", NAME="usb/%k"

where "hiddev" is your usb device (see how yours is named under
/sys/bus/usb/devices/ )

place this in your /etc/udev/rules.d directory as the file 99_my.rules

to let them have effect it is most easy to reboot.

---

### Post by dchurch24 on 2011-11-09
Wow. Thanks.

However, I'm having trouble identifying the device in that path.

There are 4 usb* directories.

lsusb returns:

```

Bus 002 Device 002: ID 10cf:5500 Velleman Components, Inc. 8055 Experiment Interface Board (address=0)

```

...for this device. Is it possible that the device id that I need can be taken from there? I assume it's vender:deviceid = 10cf:5500?

---

### Post by dchurch24 on 2011-11-09
Ok, I did this:

```

dave@frontroomrevo:/sys/bus/usb/devices/2-1$ cat product 
USB K8055

```

and then modified the 99_my.rules in the rules.d directory to this:

```

KERNEL=="K8055", MODE="0666", NAME="USB/%K"

```

then logged out and back in, but still the same. I have to be root to execute it.

---

### Post by dchurch24 on 2011-11-10
Ok, thanks to Jouke74 for pointing me in the right direction.

For completeness sake, this is what I did to get it working:

lsusb
```

Bus 002 Device 002: ID **10cf:5500** Velleman Components, Inc. 8055 Experiment Interface Board (address=0)

```

I added (which was the only line in there):

```

SUBSYSTEM=="usb", ATTR{idVendor}=="**10cf**", ATTR{idProduct}=="**5500**", MODE="0666"

```

in the file /etc/udev/rules.d/99_my.rules

I think the name of the .rules file doesn't matter so much, but I'm happy to be corrected on this.

Then logged in and out, and voila! It's working without me having to be root.

Thanks guys - once again, you make this what it is! ;-)

---

