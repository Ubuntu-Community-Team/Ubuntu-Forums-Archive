---
title: "UDEV Script Execution Part 2"
date: 2011-01-30
forum: General Help
---

### Post by phanie on 2011-01-30
Guys, this is the last of my threads about UDEV (hopefully) because i think i am close to solving it. This is my rule.

> ACTION=="add", KERNEL=="sdb1", SUBSYSTEM=="block", ATTR{partition}=="1", ATTR{start}=="8192", ATTR{size}=="3936256", PROGRAM+="/home/babyjessie/draft2.sh", MODE = 0777

This is what i get when i use udevadm test, which leads me to believing that my script is being read and run.

> 
udev_rules_apply_to_event: PROGRAM '/home/babyjessie/draft2.sh' /lib/udev/rules.d/96-mann.rules:1

util_run_program: '/home/babyjessie/draft2.sh' started
util_run_program: '/home/babyjessie/draft2.sh' returned with exitcode 0

And this is the code of the script. As you can see, it is as simple as can be because i currently am in a testing mode.

> 
!# bin/bash
echo mann2x >> log.txt

As the code suggests, it creates a .txt file and places a word mann2x in it.

The problem is when i try running it by inserting a flash drive to my pc it doesnt run. But when i use udevadm test and manual ./draft2.sh execution, it works. Please help me out guys.

---

