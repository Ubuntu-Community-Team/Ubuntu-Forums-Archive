---
title: "halevt - automounting disks, etc."
date: 2009-08-16
forum: General Help
---

### Post by SiberianBear on 2009-08-16
Hello,

I am attempting to use halevt to auto-detect my USB disks, cameras, etc - but to no avail. :/

I have started up halevt and pointed it to my config file:

ps output:
my_username 20381  0.0  0.0  39056  2196 ?        Ss   22:28   0:00 halevt -c /home/my_username/.halevt/config.xml


my config.xml is attached.

I do have hal, dbus, etc running:

ps output:
108       2660  0.0  0.0  21892  1620 ?        Ss   13:35   0:14 /bin/dbus-daemon --system
my_username       8675  0.0  0.0  23824   732 tty1     S    14:49   0:00 dbus-launch --autolaunch f65ae2ef16a194d065b682c849f09578 --binary-syntax --close-stderr
my_username       8676  0.0  0.0  21388   972 ?        Ss   14:49   0:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
my_username      20762  0.0  0.0   6268   708 pts/1    S+   22:41   0:00 grep dbus
111       3295  0.0  0.1  36560  5240 ?        Ss   13:35   0:07 /usr/sbin/hald
root      3361  0.0  0.0  15816  1268 ?        S    13:35   0:00 hald-runner
root      3390  0.0  0.0  28484  2084 ?        S    13:35   0:02 hald-addon-input: Listening on /dev/input/event8 /dev/input/event3 /dev/input/event2 /dev/input/event0 /dev/input/event5 /dev/input/event1 /dev/input/event7
root      3404  0.0  0.0  28864  2536 ?        S    13:35   0:00 /usr/lib/hal/hald-addon-rfkill-killswitch
root      3415  0.0  0.0  28476  2084 ?        S    13:35   0:00 /usr/lib/hal/hald-addon-generic-backlight
root      3431  0.0  0.0  28492  2044 ?        S    13:35   0:00 /usr/lib/hal/hald-addon-cpufreq
111       3432  0.0  0.0  32392  2080 ?        S    13:35   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      3439  0.0  0.0  28484  2064 ?        S    13:35   0:00 hald-addon-storage: polling /dev/sr0 (every 16 sec)
root      4096  0.0  0.0  28476  2048 ?        S    13:35   0:00 /usr/lib/hal/hald-addon-leds
my_username      20381  0.0  0.0  39056  2196 ?        Ss   22:28   0:00 halevt -c /home/my_username/.halevt/config.xml
root     20424  0.0  0.0  28484  2056 ?        S    22:29   0:00 hald-addon-storage: polling /dev/sdb (every 16 sec)





I am using halevt-0.1.4  ...

absolutely nothing happens when I insert a USB key or anything at all.. nothing new appears in df's output, for instance.

A little help, please?

---

### Post by SiberianBear on 2009-08-17
bump.

---

### Post by SiberianBear on 2009-08-17
bump.

---

### Post by SiberianBear on 2009-08-18
bump.

---

### Post by SiberianBear on 2009-08-18
bump.

You know, I'm just going to keep on bumping this thread. Hell, I might just write a little perl web spider to do it for me, every 30 minutes.
Then when somebody does a search on google, on "halevt", they'll find this thread with 1 million bumps and no useful replies.

Throw me a bone here!

---

### Post by ladr0n on 2009-08-19
Out of curiosity, how do you think that being annoying will get you an answer faster?

---

### Post by SiberianBear on 2009-08-20
It's a social experiment for me, at this point.

I'm curious how many bumps it'll take before this forum realizes its uselessness and ceases to exist.

bump.

---

### Post by SiberianBear on 2009-08-20
bump.

---

### Post by SiberianBear on 2009-08-20
bump.

---

### Post by SiberianBear on 2009-08-21
bump.

---

### Post by SiberianBear on 2009-08-21
bump.

---

### Post by SiberianBear on 2009-08-21
bump.

---

### Post by SiberianBear on 2009-08-22
bump

---

### Post by sun2z_emily on 2009-08-30
Does pmount works for you? or using the halevt-mount manually.
Perhaps a problem in you HAL policy.

---

