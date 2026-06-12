---
title: "Resume Lockup - Need Help"
date: 2011-11-11
forum: General Help
---

### Post by dinozzo on 2011-11-11
Hello all!

I have a problem with my minimal ubuntu 11.10 install that im hoping someone will be able to help me with. The problem is the system won't always resume from suspend. By that I mean it just stops responding to anything, the screen is black, I cant ssh/ftp into it and the only way to make it useable again is to press the reset button. It doesnt always happen though, it seems totally at random that it wont wake properly. The pc is being used as a media file server, so there is no desktop - it just boots to the terminal. The only extra things I have installed is ssh, samba, vsftpd, vim and pm-utils. I have a python script based on [http://ubuntuforums.org/showthread.php?t=1423030](http://ubuntuforums.org/showthread.php?t=1423030) set to run on boot from /etc/rc.local so that if no one is using any files it will suspend. And it works well except there is no garantee that it will resume! It happens when I manually suspend with pm-suspend so its not the script. I am completely at a loss at how to go about trouble shooting/fixing this and would love some advice.

The motherboard is a Gigabyte ga-g33m-ds2r/s2
I use the onboard graphics and lan.

I tried following [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend) and got to the hash match bit which for me shows:

[    0.575260]   Magic number: 0:524:740
[    0.575268]   hash matches /build/buildd/linux-3.0.0/drivers/base/power/main.c:587

But I cant figure out which device c:587 is?

Any help would be very appreciated

Dan

---

### Post by matt_symes on 2011-11-11
Hi
> 
[    0.575260]   Magic number: 0:524:740
[    0.575268]   hash matches /build/buildd/linux-3.0.0/drivers/base/power/main.c:587

But I cant figure out which device c:587 is?

c:587 is not a device. It is the line number in the file main.c. This is a kernel driver by the looks of it.

Kind regards

---

### Post by dinozzo on 2011-11-12
Hi

Thanks for the reply. Can I fix this or is this a bug? To be honest I dont know what any of the stuff does in that debuging link, but I followed it and that is the only "hash matches" in the log file. Does it mean that that kernel driver is definately what is responable for the lock up or could it be something else?

Dan

---

