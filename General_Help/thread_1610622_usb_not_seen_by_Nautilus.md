---
title: "usb not seen by Nautilus"
date: 2010-10-31
forum: General Help
---

### Post by Cpierce on 2010-10-31
Got a Dell GX280, and it is not seeing any usb drives. The usb keyboard works fine, the usb wireless adapter works fine, and if I run "lsusb" the thumb drive is listed, but it does show up in nautilus. I reinstalled nautilus, but it didn't help. What else do I need to do  to get it to show up in nautilus so I can copy files ?

---

### Post by matsuzine on 2010-11-01
Have you tried other usb storage devices to make sure that this is not the only one that's not detected?
Also, did you try to mount it manually?

---

### Post by Cpierce on 2010-11-01
I did try 3 different usb drives, all which are seen by other Ubuntu machines. I don't know how to mount it manually. And don't want to have to do it manually each time. Would re-installing "mountall" help ?

---

### Post by matsuzine on 2010-11-01
I'm not sure, but I was asking more to get a sense of what is going on.  

Try this to find your disk:

sudo fdisk -l

Hopefully it shows up as something like /dev/sdb1.

Next try:

sudo mkdir /media/usbdrive
sudo mount /dev/sdb1 /media/usbdrive

Let's see if that works for a starter.  

On a different note, does your machine have a floppy drive?

---

### Post by Cpierce on 2010-11-01
Thanks for the reply. I will try that. The machine does have a floppy drive. The computer worked as it should for a long time, detected usb drives just fine. Then when I tried the other day...........nothing.

---

### Post by matsuzine on 2010-11-02
The reason I ask about the floppy is I understand there is a known bug related to floppy drives and usb:

[http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html]("http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html")

Don't know if that's what's going on, but might be worth a shot.  I have no floppy drive anymore, so can't test it myself...

---

### Post by rhy7s on 2010-11-02
I've got the same issue in a fresh 10.10 install with updates. The system is an IBM ThinkCentre M/T 8172. Plugging in a USB drive shows no activity light and the drive does not mount. I've tried disabling the diskette drive, disabling USB KB/Mouse at boot, physically detaching the floppy drive and running sudo modprobe -r floppy. If I run lsusb the drive will mount shortly thereafter, it is also mounted if left plugged in at boot. Anything else I should try?

---

### Post by tajiknomi on 2010-11-02
[SIZE=2]*Try **Mount-manager.**.*[/SIZE]....

---

### Post by rhy7s on 2010-11-02
Mount manager cannot see the device either until running lsusb so it's not that useful. Since the last post I've tried commenting out the floppy from fstab and disabling automatic login as I've noticed the plugged in drive shows up when resuming from suspend. No luck so far though.

---

### Post by Cpierce on 2010-11-02
I feel that my issue is from an update as well. You computer worked properly for a year prior. If my usb drive is left in at boot, it is still not seen. 
Really hoping someone knows how to fix this.

---

### Post by fragos on 2010-11-02
Works for me. There is an option for making mounted volumes, like USB memory sticks, visible on the desktop as icons. You can set that with the Configuration Editor-> apps-> Nautilus-> desktop-> volumes_visible. Nautilus-> preferences-> has media_automount and media_automount_open which I also have set.

---

### Post by rhy7s on 2010-11-02
Yeah, it works like that for me on other computers, but this one has to have the drive plugged in at boot or during a suspend/resume cycle, or it will show up after running lsusb. It seems like on this hardware the USB ports aren't being polled for new events.

---

### Post by Cpierce on 2010-11-02
I got it fixed. I checked the link posted by Matsuzine. My BIOS didn't have a legacy support setting, so I turned the usb controller setting to "no boot", and that fixed it.

Thank you everyone.

---

