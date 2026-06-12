---
title: "I can't figure out how work ADB. (SDK)"
date: 2010-09-14
forum: General Help
---

### Post by hortstu on 2010-09-14
I downloaded SDK for linux. I extracted it to my home folder.  I've tried putting commands in the terminal but I'm getting an error message.

> 
mike@mike-laptop:~$ ./adb devices
bash: ./adb: No such file or directory
mike@mike-laptop:~$ 

> mike@mike-laptop:~$ adb shell rm /data/local/rights/mid.txt
No command 'adb' found, did you mean:
 Command 'cdb' from package 'tinycdb' (main)
 Command 'gdb' from package 'gdb' (main)
 Command 'aub' from package 'aub' (universe)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'zdb' from package 'zfs-fuse' (universe)
 Command 'mdb' from package 'mono-debugger' (universe)
 Command 'tdb' from package 'tads2-dev' (multiverse)
 Command 'pdb' from package 'python' (main)
 Command 'jdb' from package 'openjdk-6-jdk' (main)
 Command 'ab' from package 'apache2-utils' (main)
adb: command not found
mike@mike-laptop:~$ 

I'm thinking I just don't have the file in the right place?  I have it in home folder> androidsdk> tools> adb

 I need adb in order to root my evo. No I don't have access to a windows computer.  

I'm using 10.04.

Can anyone help me figure out how to get adb setup?

Thanks,
Mike

---

### Post by hortstu on 2010-09-14
I tried this... think it's progress but not sure where to go from here. I NEED A GUI!


```
mike@mike-laptop:~$ AndroidSDK/tools/adb devices
* daemon not running. starting it now on port 5037 *
* daemon started successfully *
List of devices attached

mike@mike-laptop:~$ 
```

---

### Post by hortstu on 2010-09-14
I think I got it but now what? Anyone?

```
mike@mike-laptop:~$ AndroidSDK/tools/./adb devices
List of devices attached 
HT06FHL05655    device
```

---

### Post by gitanojr on 2010-10-08
> **hortstu said:**
> I think I got it but now what? Anyone?

```
mike@mike-laptop:~$ AndroidSDK/tools/./adb devices
List of devices attached 
HT06FHL05655    device
```

How did u get it to detect your device?? been trying for hours and nothing, it does detect the emulator but not my g1, any ideas?? im running the latest ubuntu....

---

