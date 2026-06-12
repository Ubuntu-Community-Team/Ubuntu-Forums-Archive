---
title: "Creating image backup of ubuntu/variants?"
date: 2009-08-29
forum: General Help
---

### Post by MuffinMan123 on 2009-08-29
I am new to ubuntu system in general, but I am sure there are ways to create an image backup of the OS.

basically here's my goal: after I fresh instilled everything, I want to create an image of all the current setting, folder mappings, user names, configurations, software, blah blah such that I could use a bootable disk to restore the OS using the image file if something happens

---

### Post by theozzlives on 2009-08-29
> **MuffinMan123 said:**
> I am new to ubuntu system in general, but I am sure there are ways to create an image backup of the OS.

basically here's my goal: after I fresh instilled everything, I want to create an image of all the current setting, folder mappings, user names, configurations, software, blah blah such that I could use a bootable disk to restore the OS using the image file if something happens

remastersys

---

### Post by scouser73 on 2009-08-29
You shouls have a look at [[COLOR="Red"]**Remastersys**[/COLOR]]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html")

---

### Post by xopher_mc on 2009-08-29
If you want a hammer to crack a nut you can try 

[http://clonezilla.org/](http://clonezilla.org/)

Otherwise, you can use dd to make an image of the drive 

dd if=/dev/driveyourstuffison of=/media/diskyoursavingto/mydrive.img

then to recover you can do (maybe from ubuntu live cd for example)

--WARNING THIS WILL OVERWRITE ANY DATA YOU HAVE ADDED ON THE DRIVE AFTER THE BACKUP-- 


dd if=/media/diskyoursavingto/mydrive.img of=/dev/driveyourstuffison

If you do this I recommend having separate home and system partition (though will be a few bumps making user id's the same ect)! Also you can compress the image file to take up less space. Google about dd and you should find all you need.

---

