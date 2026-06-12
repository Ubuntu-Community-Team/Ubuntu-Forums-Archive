---
title: "Chrome won't start: permission denied"
date: 2012-08-16
forum: General Help
---

### Post by LeBurt on 2012-08-16
I've seen this in another thread but then the poster wanted to know how to remnove Chrome while I'd rather have it work. Here's the deal:

[LIST=1]
[*]Wanted to try out Chrome over Chromium, see if it's any faster
[*]Downloaded the 64-bit .deb from the Google website
[*]Uninstalled Chromium, just to make sure there'd be no crossover
[*]Double-clicked the .deb and Chrome installed itself through Software Center. Success.
[*]Called up Dash, typed "Chr", the Chrome icon appeared, clicked on it
[*]Waited. Nothing happened.
[*]Clicked again.
[*]Ditto.
[*]Fired up a shell, located Chrome in /opt/google/chrome. Went there.
[*]Type ./google-chrome. Got Bash: Permission denied.
[*]Wut?
[*]ls -l, everything is root root, 755 more or less, all looks fine on the permission side
[*]Stumped
[/LIST]

In fact, no binary in that directory will launch. When I type ./google- and hit the TAB key for autocomplete to work its magig, it doesn't. The upper directories are all 755. Mind you, the /opt directory is a mount point for a secondary HD I have.

More things I tried:
[LIST]
[*]sudo ./google-chrome. No result. No chrome process started. No entry in syslog.
[*]Purged the package through synaptic and re-installed. Same problem.
[/LIST]

I thought permission problems were easy to solve but this one has me perplexed. Any ideas where else to look?

---

### Post by LeBurt on 2012-08-16
When I said everything is more or less 755, I meant:

```
leburt@ciabata:/opt/google/chrome$ ls -l
total 97956
-rwxr-xr-x 1 root root 75401896 aoû 13 22:03 chrome
-rw-r--r-- 1 root root  3845361 aoû 13 22:03 chrome.pak
-rwsr-xr-x 1 root root    19064 aoû 13 22:03 chrome-sandbox
-rw-r--r-- 1 root root      482 aoû 13 22:03 default-app-block
drwxr-xr-x 2 root root     4096 aoû 16 17:59 default_apps
-rwxr-xr-x 1 root root     1665 aoû 13 22:03 google-chrome
-rw-r--r-- 1 root root     8443 aoû 13 22:03 google-chrome.desktop
-rw-r--r-- 1 root root  2883688 aoû 13 22:03 libffmpegsumo.so
-rw-r--r-- 1 root root  6528840 aoû 13 22:03 libpdf.so
-rw-r--r-- 1 root root   564984 aoû 13 22:03 libppGoogleNaClPluginChrome.so
drwxr-xr-x 2 root root     4096 aoû 16 17:59 locales
-rwxr-xr-x 1 root root   847912 aoû 13 22:03 nacl_helper
-rwxr-xr-x 1 root root     8856 aoû 13 22:03 nacl_helper_bootstrap
-rw-r--r-- 1 root root  2469244 aoû 13 22:03 nacl_irt_x86_32.nexe
-rw-r--r-- 1 root root  2714373 aoû 13 22:03 nacl_irt_x86_64.nexe
drwxr-xr-x 2 root root     4096 aoû 16 17:59 PepperFlash
-rw-r--r-- 1 root root    11045 aoû 13 22:03 product_logo_128.png
-rw-r--r-- 1 root root      710 aoû 13 22:03 product_logo_16.png
-rw-r--r-- 1 root root     1117 aoû 13 22:03 product_logo_22.png
-rw-r--r-- 1 root root     1283 aoû 13 22:03 product_logo_24.png
-rw-r--r-- 1 root root    25264 aoû 13 22:03 product_logo_256.png
-rw-r--r-- 1 root root     1767 aoû 13 22:03 product_logo_32.png
-rw-r--r-- 1 root root     4818 aoû 13 22:03 product_logo_32.xpm
-rw-r--r-- 1 root root     3252 aoû 13 22:03 product_logo_48.png
-rw-r--r-- 1 root root     4744 aoû 13 22:03 product_logo_64.png
-rw-r--r-- 1 root root  4360650 aoû 13 22:03 resources.pak
-rw-r--r-- 1 root root   256560 aoû 13 22:03 theme_resources_standard.pak
-rw-r--r-- 1 root root    60521 aoû 13 22:03 ui_resources_standard.pak
-rwxr-xr-x 1 root root    37394 aoû 13 22:03 xdg-mime
-rwxr-xr-x 1 root root    33273 aoû 13 22:03 xdg-settings

```

---

### Post by Frogs Hair on 2012-08-16
Open the terminal and post the output of the following.```
google-chrome
```

---

### Post by LeBurt on 2012-08-16
```
leburt@ciabata:~$ google-chrome
bash: /usr/bin/google-chrome: Permission denied

leburt@ciabata:~$ ls -l /usr/bin/google-chrome 
lrwxrwxrwx 1 root root 32 aoû 13 22:03 /usr/bin/google-chrome -> /opt/google/chrome/google-chrome


```

---

### Post by Frogs Hair on 2012-08-16
I only find one thread having to do with permissions and it is from 2010. [http://ubuntuforums.org/showthread.php?t=1595389](http://ubuntuforums.org/showthread.php?t=1595389)

---

### Post by LeBurt on 2012-08-17
Yeah I'd seen that, unfortunately the method to fix it isn't quite clear and the cause remains unknown.

---

### Post by s9032g@comcast.net on 2012-08-17
Try This:

sudo mv /opt/google/chrome/PepperFlash /opt/google/chrome/PepperFlash.bak
google-chrome

---

### Post by LeBurt on 2012-08-18
```
leburt@ciabata:~$ sudo mv /opt/google/chrome/PepperFlash /opt/google/chrome/PepperFlash.bak
[sudo] password for leburt: 
leburt@ciabata:~$ google-chrome
bash: /usr/bin/google-chrome: Permission denied

```

I don't think the problem has anything to do with Chrome itself. 

Could it be that something else is blocking permission? I'm thinking AppArmor or the likes. How do I investigate that?

---

### Post by Azdour on 2012-08-20
Hi,

A longshot but have you checked the permissions of the parent directories, e.g. /opt/google and /opt/google/chrome?

---

