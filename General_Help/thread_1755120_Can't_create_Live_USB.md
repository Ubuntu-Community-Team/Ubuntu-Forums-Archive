---
title: "Can't create Live USB"
date: 2011-05-10
forum: General Help
---

### Post by polardude1983 on 2011-05-10
Ok so i have just receive a 4gb USB flash drive in the mail today. And I was wanting to make it into a live usb. when i first put it in my pc it mounted. So i tried making it a live USB by using the Startup Disk Creator in the System>Administration folder. I select the ISO and select sdh1 and hit create. After it got created it. whenever I stick the USB in it never mounts the USB. Also when I try to boot from the USB it just bypasses it and goes to the hard drive.

So I formatted it and tried doing a live USB via Unetbootin same thing happened again. I have an 8GB usb that works when I did it, but not this 4GB i just received. any help would be appreciated

---

### Post by Antarctica32 on 2011-05-10
perhaps there is an error/fault on the drive, as in it was made cheaply and doesn't work right. find out what the drive is called. If you don't know what I mean by that just ask.
MAKE SURE YOUR DRIVE IS UNMOUNTED BEFORE YOU ENTER THIS 
```
fsck /dev/sda1
``` 
And then replace /dev/sda1 with what the drive is actually called. (this is very important so if you are at all unsure just ask for help)

---

### Post by polardude1983 on 2011-05-11
.

---

