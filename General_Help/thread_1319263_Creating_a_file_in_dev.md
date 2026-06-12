---
title: "Creating a file in /dev"
date: 2009-11-08
forum: General Help
---

### Post by Psycho.mario on 2009-11-08
I want to create a file in /dev/ which has something like 
```
gzip - -c > /dev/ttyS0
```
so i can direct the output from a program to this file, which compresses it, sends it over my serial, to another computer which would be running something like: 
```
cat /dev/ttyS0 | gzip -d -f -
```
so i can send data faster over serial.
How would i go about making the file which i can direct output to so that it sends it compressed over the serial, or some other device?

Thanks

---

### Post by Psycho.mario on 2009-11-08
Bump

---

### Post by jbrown96 on 2009-11-08
You probably don't want to go about making any files in /dev. /dev is not part of your file system; it's a special file system that is created during boot. Your system analyzes the devices on your system and populates /dev/ with the necessary devices. If you run ```
mount -l
``` you will get this > udev on /dev type tmpfs (rw,mode=0755) /dev/ is a filesystem in ram, so when you reboot the system, everything in /dev/ is lost. 

I can't really figure out how to send stdout and stderr straight to tar, but you could save it to a file ```
COMMAND 2&> file.txt
```

---

### Post by Psycho.mario on 2009-11-08
I didnt quite mean dev, although i wrote that. i meant like the files in dev, becuase you can chuck allsorts at them, like i could direct the output of something directly to /dev/ttyS0. I just want to make the process of compressing it easier. I could actually put: 
```
./somecommand | gzip -c -f - > /dev/ttyS0
```
but i want to shorten it/make it easier so it would just be:
```
./somecommand > specialfile
```

Its just an idea to save me typing lots out :)

---

