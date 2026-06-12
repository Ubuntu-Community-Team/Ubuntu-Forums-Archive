---
title: "burning ubuntu .iso to disc. how?"
date: 2010-11-24
forum: General Help
---

### Post by totallynew on 2010-11-24
using nero.
burn iso
or burn bootable data disc?
i have done both and when inserted and booting from disc no operating system found!
viewed the burned disc in windows it says ubuntu blah.iso on it

---

### Post by blueridgedog on 2010-11-24
You need to burn a disk from the ISO image, not burn a data disk with the ISO image on it as a file.  

From the web:

Launch Nero.
Choose Recorder / Burn image
Browse to the location of the ISO file and select the ISO file you want to burn to cd/dvd
Check the option "Finalize CD (No further writing possible!)
Click on "Burn" now.

Other explanations of the process:

[http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=nero+burn+disk+from+iso](http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=nero+burn+disk+from+iso)

---

### Post by oldfred on 2010-11-24
You want to burn an ISO, so it installs it not just copy the ISO to a CD. I prefer using flash drives as my computers will boot flash drive. They are faster & reusable.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by sikander3786 on 2010-11-24
> viewed the burned disc in windows it says ubuntu blah.iso on it

That means you just burnt a data disc.

I've used Nero in the past and there is something that reads like Image/Backup and under it, it contains the option to Burn Image to Disc.

Or you can try an open source alternative as mentioned here.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by totallynew on 2010-11-24
multisession or finalise?

---

### Post by sikander3786 on 2010-11-24
Finalize, as posted already.

> Check the option "Finalize CD (No further writing possible!)

---

### Post by totallynew on 2010-11-24
ffs. tried every burning program and method listed!
operating system not found
what am i doing wrong?

---

### Post by sikander3786 on 2010-11-24
> **totallynew said:**
> ffs. tried every burning program and method listed!
operating system not found
what am i doing wrong?
Pop in your CD and navigate to the CD drive using Windows Explorer. What files do you see in there?

And did you change the boot device from Bios to make your CD Drive first boot device?

---

### Post by totallynew on 2010-11-24
yes changed to boot cd first
files coming up

---

### Post by totallynew on 2010-11-24
none showing in windows

---

### Post by totallynew on 2010-11-24
hmmm seems like it goes through the motions of burning. verify the burn . comes back ok. but the disc is blank still

---

### Post by sikander3786 on 2010-11-24
> **totallynew said:**
> hmmm seems like it goes through the motions of burning. verify the burn . comes back ok. but the disc is blank still
Do you mean the disc is empty?

Please refer to this if Nero is unable to burn a disc for you (I know it should burn successfully but if it is not, try an alternative). Burn the disc at lowest possible speed (I use 4X).

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

And prior to that, I would recommend to check the image's integrity first so you don't run into more problems afterwards.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

And you sure your CD/DVD writer is ok?

---

### Post by totallynew on 2010-11-25
no joy. can someone send me a disc please
did the checksum stuff etc all ok

---

### Post by kelvin spratt on 2010-11-25
If you are using Vista/win7 right click on image file scroll down to write to disc and double click if you have a disc loaded it will then burn the image to disc.

---

### Post by coffeecat on 2010-11-25
Or go back to the Burning ISO Howto link that sikander3786 posted and follow the instructions to download, install and run the free Infra Recorder.

---

### Post by totallynew on 2010-11-25
must be my recorder did 40 discs and not one worked
used every kind of program too all those listed in this thread

---

### Post by totallynew on 2010-11-26
up
got a mem stick on order . way to go?

---

### Post by t4thfavor on 2010-11-26
If using windows, try ImgBurn, it's a wonderful, free alternative to nero (for burning iso's). After installing it, you just right click the iso, and click burn to disk. Simple as pie!

If you have an Ubuntu box with a burner available the right click/burn option is already there.

The flash drive will require unetbootin (or an already working live session), which is also really easy to use, at least on Linux, which is the only place I have used it.

---

### Post by sikander3786 on 2010-11-27
> **totallynew said:**
> up
got a mem stick on order . way to go?
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Or use unetbootin as advised above.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

### Post by totallynew on 2010-12-05
got the unetbootin and installed a usb bootable iso to usb stick all looks good no errors. when i put the stick in a usb slot with windows running i can run the live cd version etc but when telling my laptop to boot from usb first it does not!
?????

---

### Post by owiknowi on 2010-12-05
Is your USB device set as bootable?
To check: boot from a GParted CD, choose the USB device and look if the flag 'boot' is set. If not, do so)?

Or does your BIOS not support booting from USB (same problem here with poor BIOS in new PC)?

---

### Post by totallynew on 2010-12-05
tried another laptop. bingo :D
just need to get wireless card working now :popcorn: dell inspiron 6000 with proset wireless

---

