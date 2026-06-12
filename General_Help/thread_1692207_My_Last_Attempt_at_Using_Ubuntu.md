---
title: "My Last Attempt at Using Ubuntu"
date: 2011-02-21
forum: General Help
---

### Post by cmw000 on 2011-02-21
Ok guys, this is my last attempt to try using Ubuntu on my netbook.  I've been trying for weeks to get help to my problem of wireless networks not being detected and since I couldn't figure that out, I tried installing another distro, which didn't work.  Now when I try to reinstall Ubunutu Netbook Remix, and my netbook recognizes the USB drive is there, but when I try to boot from it, the screen goes black for a moment and then continues to the failed distro install.

I'd really like this to work.  Please help if you have any ideas.

I have an msi L1350 netbook and I'm trying to install Ubuntu Netbook Remix using the instructions for Mac found on the Ubuntu Netbook Remix website.

---

### Post by CHRSB on 2011-02-21
> **cmw000 said:**
> Ok guys, this is my last attempt to try using Ubuntu on my netbook.  I've been trying for weeks to get help to my problem of wireless networks not being detected and since I couldn't figure that out, I tried installing another distro, which didn't work.  Now when I try to reinstall Ubunutu Netbook Remix, and my netbook recognizes the USB drive is there, but when I try to boot from it, the screen goes black for a moment and then continues to the failed distro install.

I'd really like this to work.  Please help if you have any ideas.

I have an msi L1350 netbook and I'm trying to install Ubuntu Netbook Remix using the instructions for Mac found on the Ubuntu Netbook Remix website.

On that netbook you should run Ubuntu 10.10 gnome. (I hope you were at least trying to install 10.10 but seems like everyone else on this forum you like us to guess what version you are trying to install)) The UNR version sucks and you can get much more screen real estate using the desktop version.

If you have trouble with the wireless, install it on the wired network and then update the system. Then you can update the kernel to 2.6.36
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/)

Attached are some screen shots of my desktop.

---

### Post by rockager on 2011-02-21
have you hash-checked the .iso image which you downloaded? if not i would recommend you to do so as incomplete downloads or data downloading errors can render your ubuntu .iso image useless.

the first link contains hashes for different versions and variations of ubuntu & the second tells you how to hash-check if you don't know how to go about it.

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

hope this helps.

p.s i have a Samsung N150 Plus net-book and ubuntu 10.04 net-book remix works perfectly on it.
p.p.s i disagree with CHRSB on his statement that Ubuntu Netbook Remix 'sucks' .
for one thing it's got the new unity interface that is not present in the desktop edition which saves
vertical space while compromising on horizontal space, besides the unity interface will be present in the new LTS too.

---

### Post by cmw000 on 2011-02-21
CHRSB, thank you for your suggestion, but I'm not interested in installing a different distro.  You may think Ubuntu Netbook Edition "sucks," but I like it, which is why I've chosen to install it. Additionally, I don't think using a different distro will solve my issue as the issue is that my netbook will not boot from a usb drive, at all.

Sorry for not including the version I'm using.  I am trying to install the latest version, which is 10.10.

rockager, thanks for the suggestion.  Unfortunately, I've checked the checksum and they match. (That would just be too easy, wouldn't it?)

---

### Post by whatthefunk on 2011-02-21
You could try a Live CD.

---

### Post by cmw000 on 2011-02-21
My netbook is an msi L1350 and it does not have a cd drive.

---

### Post by amsterdamharu on 2011-02-21
Does it boot from usb if you use unetbootin and put tinycore on it. Tinycore is 10mb iso that is fast to download and put on a usb, when you use unetbootin then the other data on the usb drive should be save.

If it doesn't start tinycore than it could be the usb stick, I have had machines not boot off usb sticks that work perfectly fine on others and spent hours trying to get the bios to get it to boot.

What you should see is isolinux or syslinux boot and normally you have to press enter, after that you should see a menu. 

A way to see if it will boot from usb is to disable all boot devices except usb, you should get a message that there is no boot device if the computer has trouble with the usb device but then again I've seen computers that completely ignored my settings and happily booted off the harddisk anyway.

---

### Post by matt_symes on 2011-02-21
Hi

Can you try the LiveUSB in a different computer to make sure the issue is not with the LiveUSB ?

Kind regards

---

### Post by cmw000 on 2011-02-21
amsterdamharu, thanks for all the info.  I can't try a lot of that because my main machine is a mac.

But I think you and matt_symes both hit on something in isolating the usb stick.

I tried booting into it from my mac and I had the same problem.  On the netbook, the usb drive appears in the bootlist but fails to boot.  On my mac, the usb drive does not appear in the boot list at all.  

However, I have used this usb drive to install Ubunutu on this netbook before.  Is it possible I screwed up the usb drive somehow? How can I do a complete format to ensure there are no problems?

---

### Post by mastablasta on 2011-02-21
> **cmw000 said:**
> CHRSB, thank you for your suggestion, but I'm not interested in installing a different distro. You may think Ubuntu Netbook Edition "sucks," but I like it, which is why I've chosen to install it. Additionally, I don't think using a different distro will solve my issue as the issue is that my netbook will not boot from a usb drive, at all.
 
 
he is suggesting you to try Ubuntu because Netbook edition uses unity interface which at this point is still in beta and is giving problems to the users.
 
if the USB is not recognised at boot there are only two options. 
1. something is wrong with the image on your boot disk (a corrupted file, corrupted USB key, USB was made in a wrong way)
2. something is wrong in BIOS/hardware that it can not recognise the boot disk. i guess the computer can otherwise boot from USB (you have this option right?). perhaps stick in the USB and then on boot go to BIOS to see if you can see the USB.

---

### Post by cmw000 on 2011-02-21
Thanks, mastablasta.  I think you're right.  Something is probably wrong with the usb drive.  I followed the instructions well (3 times actually) so I think there must be something wrong with the usb stick.  I have no idea how to fix a usb stick though. :-s

---

### Post by whatthefunk on 2011-02-21
Reformat it and then try saving normal files on it.  If that works, the actual USB stick is probably okay.

---

### Post by cmw000 on 2011-02-21
I formatted it and put some files on it and it seems to be working fine.  So... anyone know what I should do next?

---

### Post by matt_symes on 2011-02-21
Hi

What program are you using to create the LiveUSB ? On what operating system ?

Kind regards

---

### Post by cmw000 on 2011-02-21
I'm using diskutil as per the instructions on the Ubunutu website for creating a Usb drive on a mac.

---

### Post by matt_symes on 2011-02-22
Hi

I'm not sure why diskutil is not working correctly. Maybe you could try unetbootin under wine to create the bootable USB.

Unfortunately i don't own a Mac at the moment so i may not be much help.

Kind regards

---

