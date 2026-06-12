---
title: "Cant access tty job control turned off"
date: 2010-07-22
forum: General Help
---

### Post by heavylifting on 2010-07-22
I am getting the following error after booting my Ubuntu machine. Worked fine recently and after I upgraded some stuff when I rebooted the machine I got a green screen then hit an arrow key and got the following error message:

Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/129709c0-ab0d-4426-874b-ab93336c50ae does not exist. Dopping to a shell!


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

I am running Ubuntu 10.04 and I think I installed Wine before I rebooted and updated some other software. I have googled all over and haven't found a solid solution. I went to the following website which recommended I change boot priority which I did, making the Hard Drive #1. Also, it mentioned to put in a floppy disk and that was another workaround that several people stated worked. I don't have a floppy drive so I put in a USB stick and upon boot I was actually able to see my Ubuntu loading screen but unfortunately it errored out on me again. Any advice or direction would be great, and if this is in the wrong section I apologize, still trying to make my way around.

[http://www.utheguru.com/solution-ubuntu-linux-binsh-cant-access-tty-job-control-mode-off-error]("http://www.utheguru.com/solution-ubuntu-linux-binsh-cant-access-tty-job-control-mode-off-error")

Thanks

---

### Post by heavylifting on 2010-08-10
Well I never figured out how to fix this issue. I know that it spawned after a distribution update. I ended up just reformatting.

---

