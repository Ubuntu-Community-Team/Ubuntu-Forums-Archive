---
title: "Backup main partition (Ext4)"
date: 2010-07-05
forum: General Help
---

### Post by Vexiphne on 2010-07-05
Hi.

For the 11'th hundred time I've re-installed ubuntu on my computer. Don't ask why... Let's just say that I'm still learning and done some **tiny** "mistakes" ;) 

Anyhow. I re-installed ubuntu and now I want to make an image of my main partition. /Home is on another partition. 

How do I as a beginner do this? Is there any free software for ubuntu I can use. Love the Live CD, but couldn't find any tools for making backup of an Ext4 partition. PartImage could only make image of Ext3. 
When I had windows I used Acronis True Image, but with that I can't make a boot usb. And I need to do this from a USB. Have no CD/DVD anymore.

---

### Post by btindie on 2010-07-05
You might want to take a look at [Parted Magic]("http://partedmagic.com/") which includes Clonezilla amongst other disk tools.

---

### Post by User Abuser on 2010-07-20
I think you should be able to put Acronis bootcd on a usb. If you don't know how to do it, just download a bootable usb with ATIH. Consider that support for ext4 is yet to come in ATIH2011 which is only in first stage beta. PM me if you would like me to help you find such a LiveUSB.
As for now, prolly you're best choice would be . I used it twice till now and it seemed fast, fairly easy and recovered my root without a glitch.[http://clonezilla.org/clonezilla-live/liveusb.php]("http://clonezilla.org/clonezilla-live/liveusb.php")

---

### Post by Vexiphne on 2010-07-21
Thank you User Abuser :)

---

### Post by Mark Phelps on 2010-07-21
Being a longtime user (should say now, ex-user) of Acronis products, I would recommend that avoid them like the plague!!

They have a very nasty habit of releasing buggy software (their own support forums bear this out), and you do NOT want to be relying on that stuff to be able to restore your partition.

Instead, I heartily recommend Clonezilla.  I've been using it ever since Ext4 because the defacto filesystem for Ubuntu and have found it to work great!

---

### Post by User Abuser on 2010-07-21
Although I agree that Acronis tends to stick to "Don't use till SP1" policy it never failed me even once through years of usage in terms of backup and restoration of NTFS. I didn't ever used it on linux fs. So when they finally release ATIH2011 I'll put it to the test far and wide.
Also I have found that Mondo rescue and R-Drive Image have ext4 support, but I dont know nothing about them. As well as rsync

---

