---
title: "Locked out of grub2!"
date: 2009-11-12
forum: General Help
---

### Post by wcGary83 on 2009-11-12
Hi all!

I screwed up...  I have a dual boot jaunty and karmic (because my laptop monitor doesn't work in karmic, waiting for that update...)

I set grub2 to default to jaunty, then mistakenly set timeout to 0, figuring I could still hit shift to get into the menu... nope! It says loading grub then goes straight to jaunty... 

The problem is I can't run the update-grub script from jaunty!

Help!!!

Thanks!
Gary

---

### Post by drs305 on 2009-11-12
If you cannot stop the boot process, here is what I would do:

From jaunty you should be able to mount your karmic partition. Once you do that, open a root browser and go to karmic's /boot/grub/grub.cfg  
Although I don't advocate this for most things. probably the easiest is to make it writable (right click, Properties and change it) and edit it. Then find this line and change the value to **10** or so or even -1:
> 
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=**0**
fi

You could also change the default boot value in the - set default="0" - line if you know karmic's menuentry value.
Save the file and reboot and hold down the SHIFT key. 

Once you have rebooted into Karmic, open /etc/default/grub and make the changes permanent, then run "sudo update-grub".

---

### Post by wcGary83 on 2009-11-14
Thank You, thats a great idea!

---

