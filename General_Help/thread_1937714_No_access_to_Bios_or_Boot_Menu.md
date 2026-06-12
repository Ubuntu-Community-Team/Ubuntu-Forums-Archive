---
title: "No access to Bios or Boot Menu"
date: 2012-03-08
forum: General Help
---

### Post by minimeeks on 2012-03-08
Hi. I have Ubuntu 11.10 installed on a Toshiba Satellite L645D. I am trying to run a live CD of Mint 12. I cannot access my bios menu or my boot menu. Whenever I hit the power button, it immediately bounces directly into loading ubuntu - I get the purple screen. Pushing F1, F2, F12, Del, or Esc only makes it beep. Once I managed to get the GRUB loader... but I'm not sure how,and it didn't help anyway. I saw another thread that sounded exactly the same, but that fix (unplug, remove battery, and hold power button to cycle) didn't work either.
Somehow or another, something has hijacked my boot processes, and I'd like to get it back. 
I'm not exactly new to Ubuntu, but I'm not very knowledgeable either, so please assume I don't know how to do whatever I need to do.
Thanks!

---

### Post by winh8r on 2012-03-08
This may or may not be the case for your Toshiba , but on those that I have owned there is a Toshiba splash screen that appears as you switch it on.

Along the bottom of this screen are various icons which can be selected by using the left and right arrow keys on your keyboard.

When you switch the machine on keep tapping the right arrow key and the splash screen should stay visible, then move the cursor/underline to the CD icon and the machine should boot from the cd drive.

Apologies in advance if this is not the case on your machine but it has been the method I have used on maybe four or five Toshibas I have owned in the past.

Hopwe this helps

---

### Post by Cheesemill on 2012-03-08
According to the manual for your laptop F2 should do the trick.

It is impossible for any OS to modify or disable this as the BIOS are run before anything else, even before the hard drive is detected.

I recommend just repeatedly hitting F2 as soon as you press the power button, this should get you into the BIOS.

Alternatively hitting F12 will give you the boot select screen where you can choose to boot from the CD drive.

---

### Post by minimeeks on 2012-03-08
> **winh8r said:**
> ...there is a Toshiba splash screen that appears as you switch it on.

Along the bottom of this screen are various icons which can be selected by using the left and right arrow keys on your keyboard.

When you switch the machine on keep tapping the right arrow key and the splash screen should stay visible, then move the cursor/underline to the CD icon and the machine should boot from the cd drive...


I do not get a splash screen. I tried repeatedly tapping the right arrow, but all it did was beep. Thanks, anyway.

---

### Post by minimeeks on 2012-03-08
> **Cheesemill said:**
> According to the manual for your laptop F2 should do the trick.

It is impossible for any OS to modify or disable this as the BIOS are run before anything else, even before the hard drive is detected.

I recommend just repeatedly hitting F2 as soon as you press the power button, this should get you into the BIOS.

Alternatively hitting F12 will give you the boot select screen where you can choose to boot from the CD drive.

F2 does nothing but make my computer beep at me. I agree that my OS shouldn't be messing with my Bios access... but something is preventing me from being able to access it. I've tried mashing and repeatedly tapping the ESC, DEL, F1, F2, F12 and C keys, and none of them do anything.

It seems that the second I hit my power button, it's already loading ubuntu... like a fast boot I can't kill or something.

---

### Post by minimeeks on 2012-03-08
Apparently, pushing F2 needed to begin BEFORE the power button... I got it now, though.
Thanks again for the help.

---

