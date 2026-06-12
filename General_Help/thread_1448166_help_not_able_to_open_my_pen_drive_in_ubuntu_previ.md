---
title: "help not able to open my pen drive in ubuntu??? previously opened in win vista..."
date: 2010-04-06
forum: General Help
---

### Post by amit.neo2000 on 2010-04-06
hello everybody,
i usually use my pendrive in windows vista but when today i tried to open it in ubuntu 9.10 it does not show up. i know that it is mounted because i could see it in the "USB START UP DISC CREATOR" (IN SYSTEM->ADMINISTRATION->USB START UP DISC CREATOR) [See the screen shot. ].
i think since i had never tried to open my Pen drive in ubuntu before and always open it in win vista, that's why this problem is coming up.
please suggest a way to solve my problem.
because my win vista had crashed and not starting up...
thank you.

---

### Post by -humanaut- on 2010-04-06
Download Gparted this has happened to me a couple of times. unmount and format to fat32 then reload usb-creator and it should be detected.

---

### Post by amit.neo2000 on 2010-04-06
but i cant loose data in it.
i think the data would be lost after formatting...

---

### Post by -humanaut- on 2010-04-06
yeah. thats a bit of a problem

---

### Post by -humanaut- on 2010-04-06
Can you shrink the filesystem on it and create a new one? should be able to preserve your data that way

---

### Post by amit.neo2000 on 2010-04-06
can u tell me how to do that please...

---

### Post by 2hot6ft2 on 2010-04-06
Find ANY windows machine and plug it in. Then properly unmount it using the Safely Remove Hardware function. Or shut the windows machine down properly with it still in.

When you pull it out without unmounting it using the Safely Remove Hardware function windows still has it locked which is what happened when windows crashed.

---

### Post by amit.neo2000 on 2010-04-06
thanks i'll try it...

---

### Post by 2hot6ft2 on 2010-04-06
Ubuntu also has an unmount feature which should be used before unplugging usb drives. You should always unmount a drive first to avoid that problem as well as data corruption if it's still writing to the device.

Here's a screenshot showing the unmount for ubuntu. It looks like a eject icon does on a DVD, CD or VHS player. the tip of the mouse pointer is on it.

---

### Post by amit.neo2000 on 2010-04-06
:guitar:


well at last i had to format my pen drive....   :biggrin:

I am a bit upset b'cos of the data loss but at least i learnt some thing...   ):P

thanks all of you...    \\:D/
:lolflag:

---

### Post by -humanaut- on 2010-04-06
That's rough man. Atleast its working for you now though

---

