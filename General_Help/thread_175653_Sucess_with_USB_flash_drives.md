---
title: "Sucess with USB flash drives"
date: 2006-05-13
forum: General Help
---

### Post by aaahotdog on 2006-05-13
Being a newbie with Kubuntu, everytime I  plugged in one of my many usb flash drives I would receive an error about "An error occurred while loading media:/sda1:
The file or folder media:/sda1 does not exist."   I thought I was basically screwed.   I searched high and low for a fix to this.   Finally I closed out the error window and left my flash drive attached.   I opened Konqueror and opened my home directory,from there I went up 2 levels to media.   I opened up that folder and there is my flashdrive in plain sight.   I found that I could add/delete anything to my pendrive from here.   I did the same with another pendrive with same sucess,   However the second time I bookmarked the media folder in Konqueror.    Now anytime I want to add to the pendrive I only need to save to desktop, open Konqueror, open the proper bookmark and drag file into it.    It may be a long way to do stuff as I am new yet, but it works if anyone was frustrated like I was.   Post if it works for you tool

---

### Post by tsb on 2006-05-13
you may just need to "sudo mkdir /media/sda1/" to solve the problem, but I'm just a newb myself.  you can just delete the folder using "kdesu konqueror" and navigating to the directory if it doesn't help

---

### Post by tarakan on 2006-05-13
Have a look at 
[http://kubuntuforums.net/forums/index.php?topic=3978.0]("http://kubuntuforums.net/forums/index.php?topic=3978.0")

Upgrading to KDE 3.5.x should fix it, at least it did the trick for me :)

---

