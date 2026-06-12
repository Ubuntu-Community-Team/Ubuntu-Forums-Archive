---
title: "External HDD mounting as group &quot;users&quot;"
date: 2012-01-18
forum: General Help
---

### Post by DocFox on 2012-01-18
I've been banging away at this all evening without success so any help welcome.

I have a USB storage device which I want to attach to my server and serve music/photos off it. Obviously will need read-write access to put new stuff on there.

Made a mountpoint called 'store':
```
ben@paprika:/mnt$ ls -l
drwxrwxr-x 2 root root  4096 2012-01-17 00:46 store
```

Added the following to my fstab:
```
#seagate 2tb drive
UUID=D682-B4A1 /mnt/store vfat defaults 0 0
```

But when I mount the drive:
```
ben@paprika:/mnt$ ls -l
drwxr-x--- 4 root users 16384 1969-12-31 19:00 store

```

ie. the group has changed to users and i lost write permissions for users. chmod doesnt work on a mountpoint which is 'active' (i know - i RTFM on this). have also tried setting umask=002, also dmask=027, fmask=137 but doesnt work.

I have no idea why this is happening. I really need to have permissions=775 for this drive. Is it a result of how the kernel mounts the drive through USB? I was thinking that maybe a udev rule could help?

Appreciate the help, guys/gals

---

### Post by deonis on 2012-01-18
did you try to do chown on /media/yourexternal hdd ?

---

### Post by DocFox on 2012-01-18
you cant chown a mountpoint
:(

---

### Post by deonis on 2012-01-18
I just did for one of my flash card. I plugged the card and did  su 'chown root /media/New_Volume' now I cannot do anything to my data on a flash card... I might be wrong, maybe I just don't know what  kind of device you are having out there, but I do not think it matters...

---

### Post by deonis on 2012-01-18
here is the proof: 

drwxr-xr-x  2 root  root  4096 2011-05-24 09:46 8247-4A28
drwx------  3 test  denis 4096 2012-01-18 23:00 denis    --  my flash card but belong to a user test  
drwxrwxrwx 23 denis denis 4096 2012-01-14 16:23 Mediabk
drwxr-xr-x  2 root  root  4096 2011-02-13 14:09 mov
drwx------  1 denis denis 8192 2012-01-17 23:26 work

and back to my property :) 

drwxr-xr-x  2 root  root  4096 2011-05-24 09:46 8247-4A28
drwx------  3 denis denis 4096 2012-01-18 23:00 denis  ----- my precious :)
drwxrwxrwx 23 denis denis 4096 2012-01-14 16:23 Mediabk
drwxr-xr-x  2 root  root  4096 2011-02-13 14:09 mov
drwx------  1 denis denis 8192 2012-01-17 23:26 work

---

### Post by deonis on 2012-01-18
you got to be kidding me ... I do not think that you fit in the discussion :)

---

