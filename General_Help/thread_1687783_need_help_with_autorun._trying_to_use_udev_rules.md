---
title: "need help with autorun. trying to use udev rules"
date: 2011-02-14
forum: General Help
---

### Post by kiddykoff on 2011-02-14
Basically what i'm trying to do is run some programs, when i have usb devices plugged in, not necessarily mounted.

1. when my phone is plugged in i want to run /usr/share/android-notifier-desktop/run.sh (a GUI, if that makes any difference)

2. when my ipod is plugged in i want to run scrobblethis /media/IPOD/.scrobbler.log & banshee-1 --redirect-log --play-enqueued %U (a non-GUI and a GUI)

I've tried to do what saw done on another thread but it's not working for me. What i have done is:

I have a file, /etc/udev/rules.d/usbrules.rules which says
```
#phone
ACTION=="add", SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", SYSFS{idProduct}=="0c01", RUN+="/usr/share/android-notifier-desktop/run.sh"
#ipod
ACTION=="add", SUBSYSTEM=="usb", SYSFS{idVendor}=="05ac", SYSFS{idProduct}=="1209", RUN+="/usr/local/my_script)"
```
i have a file, /usr/local/my_script which says (i'm just trying one program right now. I don't know how to add the second, although i think it would be just adding it on the next line.
```
#!/bin/bash
banshee-1 --redirect-log --play-enqueued %U
```

what i've done is not working. i've restarted my laptop and still, no. I know there's a way to reload the rules, but i can't remember where i found it. If someone could tell me what that is, it would be helpful.

---

### Post by kiddykoff on 2011-02-15
bump

---

### Post by tredegar on 2011-02-16
> what i've done is not working
You need to do some tests, to find out _what_ is "not working".

Edit your scripts to include something like ```
touch  /home/kiddy/my_script_ran
```
Then you can see if the scripts are even being called by udev. The timestamp on that file will tell you *when* the script ran.

The scripts are marked as executable, right?

> I know there's a way to reload the rules, but i can't remember where i found it.
AFAIK you no longer need to reload the rules, because **udev** now uses **inotify** to watch for changes to the rules, and reloads them when necessary.

> when my phone is plugged in i want to run /usr/share/android-notifier-desktop/run.sh (a GUI, if that makes any difference)
Running a GUI application makes a _big_ difference. Remember udev is running as root, so somewhere in your script you are going to have to su to your username, and grant access to your DISPLAY (which one?) before you start the application. 

Here, I cannot help you further, but you might want to look at how the udev rules that pop up the window that says "You have plugged in a  ..... What do you want to do with it?" have been written, and do something similar.

---

### Post by kiddykoff on 2011-02-17
alright i tried using a running a simple script
```
#!/bin/bash
touch /home/kurtis/my_script_ran
```

I didn't get any new file in my home folder so i tried changing the rule. I renamed the rule, 99-ipod_phone as i read in another thread. In the same thread i tried changing the subsystem from "usb" to "usb_device" it worked in neither case. i double checked the vendor and product id's. I also ran
```
sudo chmod +x /usr/local/my_script
```
and 
```
sudo chmod 755 /usr/local/my_script
```

running the script from terminal works, so something is not working with my rule.:confused:

I'm at the thread you were referring to, tredegar.
[http://ubuntuforums.org/showthread.php?p=10468662#post10468662]("http://ubuntuforums.org/showthread.php?p=10468662#post10468662")

---

### Post by tredegar on 2011-02-17
> I'm at the thread you were referring to, tredegar.
[http://ubuntuforums.org/showthread.p...2#post10468662](http://ubuntuforums.org/showthread.p...2#post10468662)
No, I did not refer you to that thread. And I have not posted to it.

There appears to be some confusion here.

---

### Post by kiddykoff on 2011-02-21
sorry about that, i think i had done a search for "You have plugged in a ..... What do you want to do with it?" or something similar and found a post in that thread that said something like that.

so yeah, i was confused :lolflag:

---

### Post by pulseplanet on 2011-03-07
I am have the same problem. 

My post is here: [http://ubuntuforums.org/showthread.php?t=1676827]("http://ubuntuforums.org/showthread.php?t=1676827")

---

