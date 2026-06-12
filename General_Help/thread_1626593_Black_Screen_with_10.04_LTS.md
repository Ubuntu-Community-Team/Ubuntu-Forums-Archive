---
title: "Black Screen with 10.04 LTS"
date: 2010-11-20
forum: General Help
---

### Post by Tourdog on 2010-11-20
I'm trying to install 10.04 as an only OS on my formatted hd.

Booting with the "burned" iso cd Bios reports the "Iso Linux Debian 200? etc.   Ubuntu's purple screen next comes up.  Upon "entering" a screen with 5 choices and at the bottom F1 thru F 6 shows up?   Choose there any one of 5 choice like "Install Ubuntu" or any other choice and the cd is busy for 2 minutes and the continuation of the dreaded black screen prevails.

My specs are shown in my signature below.  

Note it does show the Nvidea Video card.

What is a direction to go now?   I tried my 9.04 Karmic and it produced exactly the same blank screen too.

What to do ???

ed.   There appears (very faint) to be text and menu's if the mouse is scrolled around during this black screen time.  Unable to read any.................  too faint.  What tha?

---

### Post by sikander3786 on 2010-11-20
Press F6, select **nomodeset** and boot. Does it take you the desktop now?

---

### Post by Tourdog on 2010-11-20
No, tried it but I'll reboot and try again.

Doing the F6 does change the very very faint image though.... so it does recognize the command.

---

### Post by Tourdog on 2010-11-20
sikander3786,

I found the F6 (Other Options):  acpi off,  noapic, nolapic, nodmraid, nomodeset, free software only

the cursor rests on the 1 st one and arrowing it down and "enter" it on nomodeset produces an X.   Is this the deal  because on a second enter the X departs.

Using ctrl-alt-del to reboot I think reverts it back up to the acpi off.......... but I could be wrong!   Because once the reboot is done it (cursor) still shows on acpi off.  How does one get it to stick?  I'm missing something?!

Also:  Boot options eed boot= casper only- ubiquity initrd=/casper/initrd.lz quiet splash--  this line shows up when the F6 menu is up.    The subject line prints just above the F1-F6 but it is not live.   Important or not?

---

### Post by sikander3786 on 2010-11-20
So acpi=off is working for you? Does it solve the original problem?

---

### Post by Tourdog on 2010-11-20
No, nothing is solved yet.    Please read my #4.    I think the answer is close but I'm either not understanding what is needed to change with the NoModeSet under F6.

---

### Post by sikander3786 on 2010-11-20
> **Tourdog said:**
> No, nothing is solved yet.    Please read my #4.    I think the answer is close but I'm either not understanding what is needed to change with the NoModeSet under F6.
If it isn't solved yet, why would you want to make that change permanent?

Check your disc for defects. There is option on the same menu.

If it is defected, check the MD5SUM of the downloaded image.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the image is ok, try to burn a new disc at the lowest possible speed (I use 4X) and try again.

Boot options work most of the time. And as it seems to be a graphics problem, nomodeset should fix it.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

I am myself running Ubuntu on an Nvidia 6150LE chipset and never had problem like that.

Edit: Select nomodeset, when an X mark appears beside it, Esc the menu and hit Try Ubuntu.

---

### Post by Tourdog on 2010-11-20
sikander3786,


Edit: "Select nomodeset, when an X mark appears beside it, Esc the menu and hit Try Ubuntu".   unquote.


That is what I was missing!   Thank you so much!    I was going to reboot but it required the ESC first.  Thank you again!    This case is SOLVED!

---

### Post by sikander3786 on 2010-11-20
Glad to know that :-)

You might encounter the same error when you boot into Ubuntu the first time after completing the install.

You'll need to press and hold down the Shift key from your Bios menu until you see the Grub menu (boot menu for Ubuntu). Then highlighting the first entry, press 'e' to edit it. Navigate to "quiet & splash", delete them and type "nomodeset" in their place. Then press Ctrl + X to continue boot. You'll get to the desktop this time.

Once on the desktop, go to System > Administration > Hardware Drivers and install the Recommended/Current drivers from there. Then reboot and the problem will go away for ever.

Please post back when you get it working.

---

### Post by Tourdog on 2010-11-21
sikander3786,

Your post(s) have solved the dreaded "black screen".  My 10.04 LTS is fully operational.   I did the "update" with its 168 updates with some intrepidation .  Of course the "black screen" (just after the bios screen) occurred again but a reboot with the shift key and rewrite of "nomodeset" and I am up-to-date and with operating wifi, sound, video, printing etc.  

I hope others with the "black screen" after bios read your posts.   Well done!   It seemed we used to have a facility here to mark "solved" but now I cannot find it?

---

### Post by DeMus on 2010-11-21
Open the thread and just above your initial Post you see,a little bit to the right hand side, Thread Tools. Click it and Select: Mark as solved.

---

### Post by sikander3786 on 2010-11-21
> I hope others with the "black screen" after bios read your posts. Well done! It seemed we used to have a facility here to mark "solved" but now I cannot find it?

Actually it is a known issue and there have been many posts around that contain the fix. It is not my own knowledge at all :P

You can mark the thread Solved using [COLOR="Red"]**Thread Tools**[/COLOR] near the top of this page.

Happy Ubuntu-ing!

---

