---
title: "[Q] ADB not works"
date: 2012-01-12
forum: General Help
---

### Post by Vahids on 2012-01-12
Hi guys,

I have a Samsung Galaxy S I9000 phone.
it's `lsusb` output:
```
Bus 002 Device 012: ID 04e8:681c Samsung Electronics Co., Ltd Galaxy Portal/Spica Android Phone
```

but when i put the usb cable in phone and try "adb shell" its show me "device not found" 
I'm really stuck in this problem/:(

[SIZE="1"]I tried in live ubuntu and adb works like charm, but here (updated ubuntu) adb not works![/SIZE]:mad:
I just tried again and Live CD not worked too. :/

---

### Post by ptsubin on 2012-01-12
Try 
$adb kill-server
$sudo adb devices

See if your device gets listed. If so, you can use adb shell. I used to get the same issues without root privileges.

---

### Post by Vahids on 2012-01-12
Noting :( :
> 
vahid@vahid-MS-7577:~$ adb kill-server
vahid@vahid-MS-7577:~$ sudo adb devices
[sudo] password for vahid: 
* daemon not running. starting it now *
* daemon started successfully *
List of devices attached 

vahid@vahid-MS-7577:~$ 



---

### Post by ptsubin on 2012-01-12
I hope USB debugging is not disabled in your phone. As it is not working with live cd also. Did you try restarting the phone? Is adbd running in the phone?

---

### Post by Vahids on 2012-01-12
> **ptsubin said:**
> I hope USB debugging is not disabled in your phone. As it is not working with live cd also. Did you try restarting the phone? Is adbd running in the phone?
Reboot to recovery mod (phone) not worked
Reboot to Downloading mod (phone) not worked

and Yes, I ticked "usb debugind"

in Windows 7 it's work! i don't know what's wrong. maybe adb file! can u attach adb file ?

---

### Post by ptsubin on 2012-01-12
I am using the adb bundled with android-sdk-linux. From time to time I use the one gets build with the source as well. Both work for me without any issue. If you have just copied it from somewhere else, you can try installing the sdk and updating it.

---

### Post by Vahids on 2012-01-12
> **ptsubin said:**
> I am using the adb bundled with android-sdk-linux. From time to time I use the one gets build with the source as well. Both work for me without any issue. If you have just copied it from somewhere else, you can try installing the sdk and updating it.
Thanks dude!
You save me :D
when i run the file. it's print adb server is out of date and killing... and after that it's work.

THANKS THANKS THANKS... :*

---

### Post by ptsubin on 2012-01-18
Ah, you are welcome. One more reason to keep your development tools up to date.

---

