---
title: "Possible to install Jaunty on a USB flash drive?"
date: 2009-07-01
forum: General Help
---

### Post by raymondvillain on 2009-07-01
I have booted up Jaunty (32 bit) from the live CD.

I would like to install Ubuntu more or less permanently on a 4Gig USB flash drive.

Is this possible?

I do not want to make the flash drive function like a "live CD", I want Ubuntu installed on it.

If it is possible.

---

### Post by colau on 2009-07-01
> **raymondvillain said:**
> I have booted up Jaunty (32 bit) from the live CD.

I would like to install Ubuntu more or less permanently on a 4Gig USB flash drive.

Is this possible?

I do not want to make the flash drive function like a "live CD", I want Ubuntu installed on it.

If it is possible.
[http://ubuntuforums.org/showthread.php?p=6978317&highlight=installing+ubuntu+usb#post6978317](http://ubuntuforums.org/showthread.php?p=6978317&highlight=installing+ubuntu+usb#post6978317)

[http://ubuntuforums.org/showthread.php?p=6233663&highlight=installing+ubuntu+usb#post6233663](http://ubuntuforums.org/showthread.php?p=6233663&highlight=installing+ubuntu+usb#post6233663)

---

### Post by papenpj on 2009-07-01
If you only want to use USB so you don't mess with the vindoes partition, have you considered wubi? or are you planning to use it as a a recovery device on several computers?

---

### Post by colau on 2009-07-01
[http://ubuntuforums.org/showthread.php?p=4999072&highlight=installing+ubuntu+usb#post4999072](http://ubuntuforums.org/showthread.php?p=4999072&highlight=installing+ubuntu+usb#post4999072)

[http://ubuntuforums.org/search.php?searchid=61213468&pp=25](http://ubuntuforums.org/search.php?searchid=61213468&pp=25)

---

### Post by gchand7 on 2009-07-01
I had 8.04 on a 8 gig flash drive everything worked as long as the computer you pluged it into was able to boot from USB. The only thing I didn't like was internet was very slow....:( Now I have it on a 100gig portable hard drive. Can use it to get on another computer and retreive data for different reasons and even check for virus on windows partitions. As far as installing all I did was put the flash drive in boot up with cd and installed to the flash drive or portable hard drive. the plus side is you can go ahead and install all the programs you want and even do your updates. Hope this helped.

---

### Post by techrascal on 2009-07-01
i  installed ubuntu 8.10 on 160gb ext hard drive but it showed error 21 while booting up.....on ctrl+alt+del it wud reboot nd i cud select os's...but it crashed sum tym back after multiple failures...
i tried a fresh install of 9.04 but it did not complete the installation....after just finishing installation the screen goes weirdwith checkered sort of pattern of colors......and the system does not boot after i select ubuntu os in the grub....

what should i do to ensure ubuntu works fine with external hard disk....

---

### Post by papenpj on 2009-07-01
techrascal,
Does your computer support booting from usb and did you install grub on the USB drive and not the main harddrive.

I have a drive that runs puppy and never had a problem using it until I ran into an older computer thats boot from USB was "usb-zip" on the grub menu I changed hd0 to fd0 and it would start with that change.

---

### Post by techrascal on 2009-07-02
my notebook supports booting from usb but i think its priority in bios is not first....when i changed the priority to first the computer wud hang at grub loading stage 1.5.....

should i try putting my grub on external drive again  as i am sure the grub was loaded in ext drive(hd1)....

i've not tried supergrub ..is it also a potential solution..

---

### Post by C.S.Cameron on 2009-07-02
I have never had a problem installing Ubuntu to a flash drive just as if it was a normal internal hard drive, just plug in the drive, insert the live CD and run install. To be extra safe you can disable the computer's internal hard drive first.

---

