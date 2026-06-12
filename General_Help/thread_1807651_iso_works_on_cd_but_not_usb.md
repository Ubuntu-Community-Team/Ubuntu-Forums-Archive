---
title: "iso works on cd but not usb"
date: 2011-07-19
forum: General Help
---

### Post by monte001 on 2011-07-19
burning the ubuntu iso's on cd works fine, but burning the same to usb does not work.

does any one have any suggestions.

monte

---

### Post by 2F4U on 2011-07-19
How do you create the usb image? Do you use Startup Disk Creator, which is part of the liveCD or unetbootin?

---

### Post by haqking on 2011-07-19
> **monte001 said:**
> burning the ubuntu iso's on cd works fine, but burning the same to usb does not work.

does any one have any suggestions.

monte


download the version for a USB stick

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by Wayne_V on 2011-07-19
you can't "burn" an iso to a usb drive - you need to copy the files from the iso to the drive and then make it bootable.   see:  [http://tombuntu.com/index.php/2008/11/12/create-a-bootable-usb-drive-the-easy-way-in-ubuntu-810/](http://tombuntu.com/index.php/2008/11/12/create-a-bootable-usb-drive-the-easy-way-in-ubuntu-810/)

---

### Post by haqking on 2011-07-19
just download the USB version and follow instructions suppled online.

---

### Post by monte001 on 2011-07-19
thank you for your quick reply.

i used startup disk creator and unebootin to create.

the iso image was download from your suggested site.

cd was ok, but usb returns a response "vesamenu .32 : not a com32R image" .

different usb's had been tried with same response.

monte

---

### Post by haqking on 2011-07-19
> **monte001 said:**
> thank you for your quick reply.

i used startup disk creator and unebootin to create.

the iso image was download from your suggested site.

cd was ok, but usb returns a response "vesamenu .32 : not a com32R image" .

different usb's had been tried with same response.

monte

there are 2 downloads there, a CD .iso and an image for USB

did you choose the USB download ?

if you click show me how when you choose the usb radio button it will outline instructions on how to set your USb stick up

---

### Post by monte001 on 2011-07-19
thank you haqking,

i followed your suggested site, and there were only 2 iso choices, namely 1104 and 1004 lts.

the other steps were to show how to create an bootable usb, which i followed to the letter.

i cannot find image for usb stick.

monte

---

### Post by ajgreeny on 2011-07-19
> **haqking said:**
> there are 2 downloads there, a CD .iso and an image for USB

did you choose the USB download ?

if you click show me how when you choose the usb radio button it will outline instructions on how to set your USb stick up
The download is exactly the same, as far as I can see, and whether you want to use it on a CD or a USB drive, it is the same .iso file.  The is no .img file available for Ubuntu.

You just burn it to a CD as an image with brasero or k3b or whatever, or you use something like Startup-disk-creator or unetbootin to copy (burn) it to a USB drive and make it bootable.

@OP

Are you sure the iso file is a good one?  Have you checked it with the md5sum which you can find at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")

---

### Post by monte001 on 2011-07-19
thanks ajgreeny.

i used startup disk creator and also unebootin.

burning on cd works fine, but burning on usb's returned to the prompt which i had quoted above.

monte

---

### Post by haqking on 2011-07-19
> **ajgreeny said:**
> The download is exactly the same, as far as I can see, and whether you want to use it on a CD or a USB drive, it is the same .iso file.  The is no .img file available for Ubuntu.

You just burn it to a CD as an image with brasero or k3b or whatever, or you use something like Startup-disk-creator or unetbootin to copy (burn) it to a USB drive and make it bootable.

@OP

Are you sure the iso file is a good one?  Have you checked it with the md5sum which you can find at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")

yeah my bad i was assuming there was a differnt image file.

have you tried following the instructions for creating a USB key from the download page ?

---

### Post by monte001 on 2011-07-20
thank you every body.

i used startup disk creator and tried it on many versions of ubuntu.

i followed the steps in the guide.

the cd's always work, but usb never and with the above mentioned prompt returned.

i don't know what went wrong, and consider that i have done enough testings.

thanks all for your help.

monte

---

### Post by Wayne_V on 2011-07-20
you may want to review this:  [http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/](http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/)

---

### Post by monte001 on 2011-07-20
thanks Wayne_V.

the first ever bootable usb created since I tried ubuntu.

monte

---

### Post by monte001 on 2011-07-23
my apology for not marking the thread solved earlier simply because i don't know how to do that until i googled.

thanks for all your help.

monte

---

