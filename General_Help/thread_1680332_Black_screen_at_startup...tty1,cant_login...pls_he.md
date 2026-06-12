---
title: "Black screen at startup...tty1,cant login...pls help"
date: 2011-02-02
forum: General Help
---

### Post by inestimabil on 2011-02-02
Heloo, Im having a big problem....I hope somebody can help me start my laptop < i have lots of personal data) .  So my problem is: I push the start button, ubuntu logo is on the screen, but next a black screen is apearing and its written  in the left up corner Ubuntu 10.10 napoleon tty1, and right under napoleon login: ...and its stuck on this black screen
napoleon is the name of my laptop
No combination is working, ctrl+alt + F1(F7). I got the problem after I started my laptop with an Ubuntu boot cd inside, so I ejected the cd while ubuntu was starting, and pushed the off button. 
Please help....* excuse my bad english, pls...

---

### Post by Kirboosy on 2011-02-02
After taking the CD out of the drive did you try rebooting?


You could always try logging into the computer then running
```
startx
``` and see what outputs from that.

---

### Post by matt_symes on 2011-02-02
Hi

Log in at the console and type 

```
startx
```

Does that start an x session ? Are there any error messages ?

Kind regards

---

### Post by hwttdz on 2011-02-02
First is the issue you can't login or that you have no graphical environment?  What happens if you type your login name and password (you won't see stars when typing your password) at the prompt.  

Assuming you can login (more likely):
Don't worry too much, that's actually a working system and it should be quite possible to figure out what's going on.  You can actually login to that terminal and run the same commands that you might from the terminal emulator in the graphical environment.  

I would think one of the first things to do would be to look at dmesg and see if there's anything glaring in there.  I prefer to have the verbose nosplash boot, so I can see if there are any goofy errors on startup, so you might consider changing that in your grub.  Then try "sudo service gdm stop" (it'll probably give errors), then "sudo service gdm start".  If that gives any errors let us know.

If you can't login (less likely):
You're going to need to boot into single user mode and change your password.  [http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/) .  If you need to edit any of the grub config files before you get the graphical interface you should be able to use nano.  The ^X would mean ctrl+x and that should give you what you need to edit, save and exit.

---

### Post by inestimabil on 2011-02-02
After i ejected the cd I shut down the laptop using the power off button. 
I cant open a terminal window, I cant write anything on the screen. Also, when the computer starts it apears nothing on the screen, just ubuntu logo for 2 seconds and after that the black screen. Is there any combination like ctrl + alt +F1 to open a terminal window? Or if I start with a boot cd is any chance to repair it?

---

### Post by Kirboosy on 2011-02-02
> **hwttdz said:**
> If you can't login (less likely):
You're going to need to boot into single user mode and change your password.  [http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/) .  If you need to edit any of the grub config files before you get the graphical interface you should be able to use nano.  The ^X would mean ctrl+x and that should give you what you need to edit, save and exit.

^^Try this then

---

### Post by matt_symes on 2011-02-02
Hi

What happens if you boot into recovery mode from the grub menu ?

What error messages are displayed on the screen ? Take a photo of the screen and upload back here if you can.

Kind regards

---

### Post by inestimabil on 2011-02-02
So, if I hit the Enter button after the computer starts it  loads the grub screen. If I hit "E" Im getting the black screen from the first picture. If I choose to start in recovery mode the result is the second pic. In revovery it apears a blue screen with some option to choose, but only for a second...

---

### Post by matt_symes on 2011-02-02
Hi

That looks like some kind of video error. Not sure what to suggest at the moment.

The first thing i would do is back up all your personal data using the LiveCD.

Kind regards

---

### Post by inestimabil on 2011-02-02
Im trying to save my files on a usb stick, but I cant copy the files because i m not having the permission to read them. So what is the solution to save my data?

---

### Post by matt_symes on 2011-02-02
Hi

Archive your files using tar and copy to the usb. It will retain your permissions when you unpack the archive. Only copy your personal files.

[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

Kind regards

---

### Post by inestimabil on 2011-02-02
I saved the files I need. Im waiting for suggestions to repair the grub. 
Best regards, and thank you.

---

### Post by Kirboosy on 2011-02-02
I think the next suggestion was going to be wiping it out and reinstalling everything. Sometimes its just faster to backup everything and restart. Video issues are generally long and tedious. 


Unless you are dead set on fixing your issue without reinstalling. Have you recently installed any new drivers or updates?

---

### Post by Sh4dounet on 2011-04-22
I juste have the same issue after updating to maverick (with issues) and re-activating my nvidia driver ( (current) ) ...

---

