---
title: "Shotwell works only as root."
date: 2011-07-06
forum: General Help
---

### Post by tajreed on 2011-07-06
I need to be root to use Shotwell. If not, I get "Shotwell was unable to upgrade photo library...". I can run it fine as root.

Any thoughts, could this be a permission problem?

---

### Post by WorMzy on 2011-07-06
Have you ever run it with "sudo"?

If so, then yes, it's quite likely that there's a permissions problem. You should never run graphical applications with sudo. Use "gksu" or "gksudo" instead. Just use "sudo" for console applications. :)

Run the following command to fix the problem:
```
sudo chown -R $USER:$USER /home/$USER
```

Copy and paste the command, or be very careful when writing it out. "sudo chown -R" can have disastrous effects on your system if you run it on the wrong folder.

---

### Post by tajreed on 2011-07-06
I have been running it with gksu, have not used sudo. Should I still run that command?

---

### Post by WorMzy on 2011-07-06
It couldn't hurt. But first, what does
```
find ~ -iname "*shotwell*" -exec ls -la {} \;
```
say?

---

### Post by tajreed on 2011-07-06
Here it is:

drwxr-xr-x  6 root root 4096 2010-12-23 11:02 .
drwxr-xr-x 82 duke duke 4096 2011-07-06 17:52 ..
drwxr-xr-x  2 root root 4096 2011-01-16 17:02 data
drwxr-xr-x  2 root root 4096 2010-10-14 17:25 mimics
drwxr-xr-x  4 root root 4096 2010-10-14 17:25 thumbs
drwxr-xr-x  2 root root 4096 2010-12-23 11:03 wallpaper
-rw-rw-rw- 1 root root 1117 2010-07-31 09:33 /home/duke/.config/ubuntu-tweak/appcenter/appcenter/logo/shotwell-icon.png
-rwxrwxrwx 1 root root 4344 2010-07-31 09:33 /home/duke/.config/ubuntu-tweak/appcenter/appcenter/logo/shotwell-logo.png
total 20
drwxr-xr-x  5 root root 4096 2010-12-01 18:02 .
drwxr-xr-x 53 duke duke 4096 2011-05-28 20:24 ..
-rw-rw-rw-  1 root root    0 2010-10-14 17:26 %gconf.xml
drwxr-xr-x  4 root root 4096 2010-10-14 17:38 preferences
drwxr-xr-x  2 root root 4096 2011-01-16 17:06 printing
drwxr-xr-x  2 root root 4096 2010-12-23 10:57 sharing
total 12
drwxr-xr-x  2 root root 4096 2010-10-14 17:25 .
drwxr-xr-x 33 duke duke 4096 2011-07-06 10:29 ..
-rw-rw-rw-  1 root root  656 2011-07-06 18:01 shotwell.log
-rw-rw-rw- 1 root root 656 2011-07-06 18:01 /home/duke/.cache/shotwell/shotwell.log
-rw-r--r-- 1 duke duke 8742 2011-07-05 18:24 /home/duke/.cache/software-center/rnrclient/reviews.ubuntu.com,reviews,api,1.0,reviews,filter,en,ubuntu,natty,any,shotwell,page,1,,218860b6a0de18c51abc0de1ac309d97
-rw-r--r-- 1 duke duke 8926 2011-07-05 20:22 /home/duke/.cache/software-center/rnrclient/reviews.ubuntu.com,reviews,api,1.0,reviews,filter,en,lp-ppa-yorba,natty,any,shotwell,page,1,,8aa0c4fe99575618d85563c4eb4300c9
duke@duke-System-Product-Name:~$

---

### Post by WorMzy on 2011-07-06
> **tajreed said:**
> Here it is:

```
drwxr-xr-x  6 root root 4096 2010-12-23 11:02 .
drwxr-xr-x 82 duke duke 4096 2011-07-06 17:52 ..
drwxr-xr-x  2 root root 4096 2011-01-16 17:02 data
drwxr-xr-x  2 root root 4096 2010-10-14 17:25 mimics
drwxr-xr-x  4 root root 4096 2010-10-14 17:25 thumbs
drwxr-xr-x  2 root root 4096 2010-12-23 11:03 wallpaper
-rw-rw-rw- 1 root root 1117 2010-07-31 09:33 /home/duke/.config/ubuntu-tweak/appcenter/appcenter/logo/shotwell-icon.png
-rwxrwxrwx 1 root root 4344 2010-07-31 09:33 /home/duke/.config/ubuntu-tweak/appcenter/appcenter/logo/shotwell-logo.png
total 20
drwxr-xr-x  5 root root 4096 2010-12-01 18:02 .
drwxr-xr-x 53 duke duke 4096 2011-05-28 20:24 ..
-rw-rw-rw-  1 root root    0 2010-10-14 17:26 %gconf.xml
drwxr-xr-x  4 root root 4096 2010-10-14 17:38 preferences
drwxr-xr-x  2 root root 4096 2011-01-16 17:06 printing
drwxr-xr-x  2 root root 4096 2010-12-23 10:57 sharing
total 12
drwxr-xr-x  2 root root 4096 2010-10-14 17:25 .
drwxr-xr-x 33 duke duke 4096 2011-07-06 10:29 ..
-rw-rw-rw-  1 root root  656 2011-07-06 18:01 shotwell.log
-rw-rw-rw- 1 root root 656 2011-07-06 18:01 /home/duke/.cache/shotwell/shotwell.log
-rw-r--r-- 1 duke duke 8742 2011-07-05 18:24 /home/duke/.cache/software-center/rnrclient/reviews.ubuntu.com,reviews,api,1.0,reviews,filter,en,ubuntu,natty,any,shotwell,page,1,,218860b6a0de18c51abc0de1ac309d97
-rw-r--r-- 1 duke duke 8926 2011-07-05 20:22 /home/duke/.cache/software-center/rnrclient/reviews.ubuntu.com,reviews,api,1.0,reviews,filter,en,lp-ppa-yorba,natty,any,shotwell,page,1,,8aa0c4fe99575618d85563c4eb4300c9
duke@duke-System-Product-Name:~$
```
There's an awful lot of files owned by root there. So yes, run the chown command. Make sure you're extra vigilant about using gksu or gksudo with graphical apps, it looks like you may have accidentally used sudo with a couple of them at least once, and that's all it takes. :)

---

### Post by tajreed on 2011-07-06
Tried the chown command, "permission denied"

---

### Post by tajreed on 2011-07-06
Got it, changed account type from "custom" to "administrator". Don't know how it became "custom".

Thanks for your time. I very much appreciate the effort.

JR

---

