---
title: "Hibernate issue in Ubuntu 11.10"
date: 2011-11-06
forum: General Help
---

### Post by Itun on 2011-11-06
I have Ubuntu 11.10 and hibernate on this doesn't work. I looked at [this post]("http://askubuntu.com/questions/66879/fix-hibernate-issue-in-ubuntu-11-10"). And after the string  " # swap was on /dev/….." I have nothing with comments. I cannot find file: /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux... More over s2disk does not work properly and computer cannot hibernate as it was with other hibernate utility which is going with native Ubuntu install pack.

---

### Post by bluexrider on 2011-11-06
> **Itun said:**
> I have Ubuntu 11.10 and hibernate on this doesn't work. I looked at [this post]("http://askubuntu.com/questions/66879/fix-hibernate-issue-in-ubuntu-11-10"). And after the string  " # swap was on /dev/….." I have nothing with comments. I cannot find file: /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux... More over s2disk does not work properly and computer cannot hibernate as it was with other hibernate utility which is going with native Ubuntu install pack.

This may be too simple. Did you check your power settings?

---

### Post by ajgreeny on 2011-11-06
Can you also show the output of the command ```
free -m
``` in terminal.  This will tell us if your swap is enabled and how big it is.

---

### Post by unadulterated on 2011-11-30
Hi there
Am using 11.10 and having the s2disk snapshotting system getting stuck and need to force shutdown and then restart to get it back to working. Its getting bad.. earlier 11.04 hibernation would work just fine. but having these issues lately. any suggestions will be greatly appreciated.

free -m gives 

sandip@sandlaptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2004       1878        126          0         96        460
-/+ buffers/cache:       1321        683
Swap:         1953          6       1946


let me know if anyy other detail is required. if you ca direct me to correct solution that would be nice too.

---

### Post by sumith_p on 2011-12-07
Try this..
sudo apt-get install uswsusp

hibernate is working for me now....:D

---

### Post by scotchie on 2011-12-21
I had the same problem. I found the following in /var/log/pm-suspend.log

```

Running hook /etc/pm/sleep.d/00xrandr.sh hibernate hibernate:
xauth:  unable to generate an authority file name
No protocol specified
Can't open display :0.0

/etc/pm/sleep.d/00xrandr.sh hibernate hibernate: Returned exit code 1.
Wed Dec 21 13:31:12 MST 2011: Inhibit found, will not perform hibernate

```The solution for me was to disable the script:

```
$ sudo chmod -x /etc/pm/sleep.d/00xrandr.sh 
```I am not an X expert, but without this script the hibernate works fine.

I would suggest finding the error in /var/log/pm-suspend.log and posting it.

You can also review the man page ("man pm-suspend") for more info about hibernation in Ubuntu.

---

