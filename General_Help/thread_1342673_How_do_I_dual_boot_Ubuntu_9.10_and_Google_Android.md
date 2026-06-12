---
title: "How do I dual boot Ubuntu 9.10 and Google Android"
date: 2009-12-01
forum: General Help
---

### Post by Vignesh S on 2009-12-01
I've heard that it is possible to install Google Android (no, not using liveandroid, I'm talking about actually physically installing Google Android) onto a netbook. I'm very interested in doing this with the Medion Akoya E1210. My question is, how would I go about making a LiveUSB to install Google Android, and then dual boot it with 9.10 (the full desktop installation version)? I'd also like to know whether its possible to upgrade version 1.5 "Cupcake" to 2.0 "Eclair" on Android.

After seeing the Acer AOD250 dual-booting with Android and Windows 7, I'm really itching to do the same with my netbook, only dual-booting Android with Ubuntu 9.10.

---

### Post by sprince09 on 2009-12-01
What you seek lies here:

[http://www.android-x86.org/download](http://www.android-x86.org/download)


Download one of the stable releases (1.6 as of this post). I just did this yesterday but I can't remember whether I used the .iso with unetbootin or the .img with usb-imagewriter to create my live-usb. Once you have the live-usb, you can install android alongside any other OS you have installed... just make sure not to overwrite your existing OS by accident!

I'm actually going to try to do exactly what you posted, but with ubuntu 9.04 & android instead of 9.10 & android. I'll post back my successes or failures.

PS: Don't forget to backup your data before trying to install anything!

---

### Post by sprince09 on 2009-12-02
Well, that was suprisingly straightforward. Keep in mind I used Ubuntu 9.04, which still uses grub. Ubuntu 9.10 uses grub 2, so the procedure for adding boot options might be different (I don't know how to use grub2, and I only just barely can use grub).

I'm using an EEEPC-1000 for all this, and I got it working just fine, so if you're using a different laptop, I'm not sure I can help...


Anyway, for Jaunty, here's the procedure:


First, back up all your data in case something goes awry.


Install Jaunty or make sure you have jaunty installed as your primary OS (or another OS that uses grub).


Now, get a live-usb stick operational (see link above). I'm faily certain you need to use the usb .img with the usb-imagewriter package from the Ubuntu repositories to create the live-usb, but I could be wrong. The unetbootin package with the cd .iso file is another possible option, but I don't remember which I used, and I don't remember which way works. One way DOES work though ;)


Now make an empty ext3 partition somewhere on your hard drive. This will be your android installation partition (use gparted to create the partition).


Now boot onto the live-usb, choose the install option.


Choose where you want to install to, just like you would on any other OS installation. Choose the empty partition you just made.


When prompted to install Grub, choose no.


Wait for android to install.


Now you can either test your installation by booting into android, or just reboot your computer and restart into ubuntu. Once you're done playing with android, reboot into ubuntu.


Now we need to edit /boot/grub/menu.lst so that we can choose to boot into android in addition to ubuntu. You'll need the UUID of the drive you installed android onto, as well as the partition number. I'll use my installation as an example. I installed android to my /dev/sdc2 partition. The UUID for /dev/sdc2 can by found by running

```
ls -alh /dev/disk/by-uuid/
```

and looking for the big nasty number corresponding to /dev/sdc2. 

```
scott@aristotle:~$ ls -alh /dev/disk/by-uuid/
total 0
drwxr-xr-x 2 root root 120 2009-12-01 23:56 .
drwxr-xr-x 6 root root 120 2009-12-01 23:41 ..
lrwxrwxrwx 1 root root  10 2009-12-01 23:40 5d1f609d-d103-47fb-ab8a-4003ed9b29a1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2009-12-01 23:41 aebc27b3-d970-4e5f-84a1-8b96d367e6b2 -> ../../sdc2
lrwxrwxrwx 1 root root  10 2009-12-01 23:56 dab9d33d-58b7-480d-a703-6c168e45b490 -> ../../sdc1
lrwxrwxrwx 1 root root  10 2009-12-01 23:40 f2ccdce6-e926-4291-bd9f-1bbf65761572 -> ../../sdb1
```


For me, /dev/sdc2 had UUID = aebc27b3-d970-4e5f-84a1-8b96d367e6b2


Alright, now open up /boot/grub/menu.lst in your favorite text editor. Scroll all the way to the bottom (after it says END AUTOMATIC BOOT LIST or something like that) and add the following, replacing my UUID with your UUID:

```
title		Android 1.6
uuid		aebc27b3-d970-4e5f-84a1-8b96d367e6b2
kernel		/android-1.6/kernel root=UUID=aebc27b3-d970-4e5f 84a1-8b96d367e6b2 androidboot.hardware=eeepc  acpi_sleep=s3_bios,s3_mode SRC=/android-1.6
initrd		/android-1.6/initrd.img
```

Note that the kernel line in that block is all one line. Also, your path to your kernel and initrd might be different from mine, but that's easy to check. Those paths are just the paths from the root of your android install partitions to the kernel and initrd.img file respectivley. So, if I mount my android partition in ubuntu, I see my android kernel and initrd.img are located as follows:

```
scott@aristotle:~$ ls /media/Android-x86/android-1.6/kernel 
/media/Android-x86/android-1.6/kernel

scott@aristotle:~$ ls /media/Android-x86/android-1.6/initrd.img 
/media/Android-x86/android-1.6/initrd.img

```


The only part of that that matters is the part after Android-x86. If you stare it long enough it should make sense....

Anyway, after you've made those changes to menu.lst, save and exit and then you should be good to go. Just reboot and choose android from the grub menu to boot into android :)


I got my info from the following websites:

Live-usb: [http://www.android-x86.org/download](http://www.android-x86.org/download)

Android Install: [http://www.android-x86.org/documents/installhowto](http://www.android-x86.org/documents/installhowto)

Grub setup (half-way down): [http://code.google.com/p/android-x86/wiki/GetSourceCode?tm=4](http://code.google.com/p/android-x86/wiki/GetSourceCode?tm=4)

Good luck!

---

### Post by Vignesh S on 2009-12-03
Whoa, I'm overloaded in information!
Yeah, I stumbled across Androidx86 too, but how on Earth do I install the USB image onto a USB to begin with? I can't seem to find usb-imagewriter anywhere (i.e. can't open it). I think it would just be easier to use UNetBootin to put the ISO onto my USB stick :-)

And yes, GRUB2 is a LOT more different to the original, but I think I know how to do it. I'm going to give it a crack

Whoa, you are saying that Androidx86 tries to install a GRUB? Wouldn't that recognise Ubuntu 9.10? Because if it did, it would be a hell of a lot easier to use instead of the method you just outlined. But if it doesn't work, it doesn't bug me. I've got copious amounts of free time now to do things like this :-)

---

### Post by sprince09 on 2009-12-03
For the USB-live stuff, I used the package usb-imagewriter which you can install with Synaptic or aptitude from the Ubuntu repositories... or at least you can in Jaunty (might need universe/multiverse enabled). The only reason I even mention that package is because I had trouble getting the .iso/unetbootin method working, but that could have just been me being dumb ;)

> Whoa, you are saying that Androidx86 tries to install a GRUB?

Yup, it does. In my case, I installed Android to a different physical hard drive than my Ubuntu OS (which also has grub installed). I wanted to be able to access both Ubuntu and Android from the same grub menu, so I opted not to install GRUB onto the 2nd hard drive because I wasn't sure if it would pick up my Ubuntu OS on a seperate drive. Instead, I edited Ubuntu's grub to look for Android on my other disk. 

If you install Android and Ubuntu onto the same drive, Android's grub *should* pick up your Ubuntu OS as well... but I could be wrong!

---

### Post by Vignesh S on 2009-12-14
Hmmm. This is quite strange. When I let Android install the GRUB, Ubuntu still showed up without any option to boot up in Android. And there's also the fact that out of the computers here, only 2 boot up Android without major dramas, and 1 of them has to boot up in VESA mode. Clearly, it doesn't like dual-core processors, more like Pentium Dual Core, which both my desktop and laptop operate with. Oh well, no matter. 

When I get around to it, I'll report on how dual-booting Android and Ubuntu 9.10 went. I think I'm onto something after reading up on some stuff about GRUB2. I'll post back on how it all went when I get around to it :-)

---

