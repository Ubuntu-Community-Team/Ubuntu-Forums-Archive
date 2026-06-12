---
title: "USB device no longer automounts"
date: 2009-11-04
forum: General Help
---

### Post by Naegling23 on 2009-11-04
I upgraded this past weekend to 9.10, and all of a sudden my usb thumbdrive, as well as any other usb storage drive no longer automount (I can still mount them manually).  How can I fix this?  Were are the settings for automounting devices?

Its not a straight up usb problem, as my usb mouse still works fine.

---

### Post by Giblet5 on 2009-11-04
Can you open a terminal window and post the output of the following command: ```
ps -ef | grep hald
```

It sounds like HAL (Hardware Abstraction Layer) isn't running.

---

### Post by Naegling23 on 2009-11-04
pangolin@ubuntu:~$ ps -ef | grep hald
111       2223     1  0 16:28 ?        00:00:00 hald --daemon=yes
root      2315  2223  0 16:28 ?        00:00:00 hald-runner
root      2455  2315  0 16:28 ?        00:00:00 /usr/lib/hal/hald-addon-leds
root      2524  2315  0 16:28 ?        00:00:00 /usr/lib/hal/hald-addon-rfkill-killswitch
root      2553  2315  0 16:28 ?        00:00:00 /usr/lib/hal/hald-addon-generic-backlight
root      2575  2315  0 16:28 ?        00:00:00 hald-addon-input: Listening on /dev/input/event1 /dev/input/event5 /dev/input/event8 /dev/input/event3 /dev/input/event2 /dev/input/event6 /dev/input/event0
root      2579  2315  0 16:28 ?        00:00:00 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      2581  2315  0 16:28 ?        00:00:00 /usr/lib/hal/hald-addon-cpufreq
111       2582  2315  0 16:28 ?        00:00:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
pangolin  5639  5563  0 16:43 pts/0    00:00:00 grep hald
pangolin@ubuntu:~$

---

### Post by synicalx on 2009-11-04
A bit random, but what brand is your USB device?

I've been testing 9.10 and I've had problems mounting a Kingston pen drive and a Channel + HDD enclosure/HDD, yet my Sony pen drive mounts just fine?

---

### Post by Naegling23 on 2009-11-04
I saw some other posts recommending installing gnome-volume-manager.  I do that, and now, when I plug the drive in, it comes up in the disk utility.  However, it is saying unrecognized, unknown or unused...wtf?  This worked prior to the karmic upgrade, and the drive works fine on my windows pc.  

One other note, I am also having trouble with my theme not loading at startup, could both of these issues be related to some sort of startup issue?

---

### Post by Naegling23 on 2009-11-04
ive tried a couple of devices, my htc touch, sony psp, and sandisk usb stick, all of them have the same problem, I can manually mount them, they just dont automount.

---

### Post by coffeecat on 2009-11-04
Other people are seeing this problem:

[http://ubuntuforums.org/showthread.php?t=1307542](http://ubuntuforums.org/showthread.php?t=1307542)

Sorry I can't be of more help because automounting of USB flash drives works just fine for me in Karmic. But if you look at post #22, you'll see that someone fixed the problem with a proposed update of udev. If you are tempted to install proposed updates, please read my post #24 in that thread and proceed with caution. If you don't and accept all proposed updates, you **will** break your system sooner or later. Having said that, if that udev update does solve the problem and if it survives the quality control of proposed, then it will eventually come through as a regular update.

---

### Post by Naegling23 on 2009-11-04
thank you coffeecat, the udev from the proposed repository fixed the problem.  To keep from breaking anything else, I immediately removed the proposed repository after updating udev only.

I have noticed a lot of people having this same problem, so, it appears to be a bug in udev, either wait for a stable update, or carefully update udev from proposed.

Good luck!

---

