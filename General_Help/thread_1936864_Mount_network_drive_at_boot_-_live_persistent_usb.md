---
title: "Mount network drive at boot - live persistent usb"
date: 2012-03-06
forum: General Help
---

### Post by castalla on 2012-03-06
Can some kind soul give me some specific (newbie level) help?

I want to mount a network server drive at boot using live persistent ubuntu.

I added:

mount -t cifs //server/folder /home/user/folder

to the fstab file.

I discovered that the change to fstab is NOT persistent on boot.

So, is there a way to make the edit to fstab persistent?  Or, can I add the command to rc.local ? 

Thanks for any help.

---

### Post by papibe on 2012-03-06
Hi castalla.

Are you able to mount the share manually?

Also, could you post the content of your /etc/fstab? I got the impression that you added that exact command instead of the proper formatted columns.

Regards.

---

### Post by castalla on 2012-03-06
Okay.

The command works in terminal and the network drive is mounted.

I added:

//server/folder /home/user/folder cifs guest,_netdev 0 0

to fstab

When I reboot the changes made to fstab are not saved - it's still the original fstab

In fact, I tested by just adding hash comments to fstab - they are gone on reboot.

So, the problem is how to make changes to fstab persistent?  Or how can I add the command to rc.local , as an alternative way to mount the drive.

I'll have to reboot into ubuntu if you want a copy of the existing fstab file.

---

### Post by papibe on 2012-03-06
What method did you use to create the live persistent usb?

Could you review the basic steps that you took?

Regards.

---

### Post by castalla on 2012-03-07
I used unetbootin - with persistence size of 500 mb

---

### Post by papibe on 2012-03-07
I didn't know you could do that with UNetBootin, and unfortunately, I don't know how to fix it either.

I've always used 'Startup Disk Creator' (usb-creator-gtk) without problems. I believe it is installed by default. I would recommend trying it out.

Regards.

---

### Post by castalla on 2012-03-07
I don't think it's easy to get working.

I just put the command in rc.local - seems to work

Thanks/

---

