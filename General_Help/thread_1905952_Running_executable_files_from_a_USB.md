---
title: "Running executable files from a USB"
date: 2012-01-08
forum: General Help
---

### Post by Black_Sirrah239 on 2012-01-08
I have a USB formatted in FAT32, and I use my usb to hold most my files because my ubuntu installation is only 7gb. The only problem is, programs on it will not execute. I have managed to get around this using shell scripts, except now I have come across something I cannot use a script to get around. 
I am trying to use the android sdk for linux. It starts fine with a shell script to launch it, except when I go Tools > Manage AVDs > (select AVD) > Start > Launch then I get this error:

Failed to start emulator: Cannot run program "/media/5072-4795/Other Programs/Android SDK/android-sdk-linux/tools/emulator": java.io.IOException: error=13, Permission denied

Anyone know how to fix?
I cannot move it onto my hard drive because I don't have enough space.

Thanks,
Black_Sirrah239

---

### Post by carranty on 2012-01-08
What have you set the permissions to on the external drive and the file?

```
ls -ld /media/5072-4795/
```

```
ls -l /media/5072-4795/Other Programs/Android SDK/android-sdk-linux/tools/emulator

```

---

