---
title: "Webcam Does Not Work"
date: 2012-04-19
forum: General Help
---

### Post by craig10x on 2012-04-19
I currently have Ubuntu 12.04 installed (though it didn't work on 11.10 either when i had that installed)...I can't get my built-in webcam to work...

My computer is a 6 month old Toshiba 17" Laptop with i3 core intel processor and intel graphics...

I installed both "Cheese" and also "Guvc" and in both cases, when i open the programs, it says "No Device Found"...

Any ideas on how to get it going?  All feedback will be appreciated... :)

---

### Post by papibe on 2012-04-19
Hi craig10x.

Some details of your camera would be helpful. Could you post the result of this command?
```
lsusb
```
Regards.

---

### Post by craig10x on 2012-04-20
Hi...thanks for trying to help...but why would i be checking the usb when it's the built in laptop webcam (not an external webcam device plugged into usb port)?

I did check it in terminal and it has some info and mentions about intel...i wanted to post it here with a screenshot, but ubuntu forums doesn't seem to allow picture attachments on the forum (only links to remote sites where you post photos)...

---

### Post by plucky on 2012-04-20
> Hi...thanks for trying to help...but why would i be checking the usb when it's the built in laptop webcam (not an external webcam device plugged into usb port)?


Built in webcams normally show up as a USB device.

> I did check it in terminal and it has some info and mentions about intel...i wanted to post it here with a screenshot, but ubuntu forums doesn't seem to allow picture attachments on the forum (only links to remote sites where you post photos)... 

You can upload screenshots as an attachment.There is a size limitation on all uploads to the forum.


Good luck

---

### Post by ki4jgt on 2012-04-20
> **plucky said:**
> Built in webcams normally show up as a USB device.



You can upload screenshots as an attachment.There is a size limitation on all uploads to the forum.


Good luck

Expanding on this, most built in webcams don't just show up as a USB but they actually are run into the inner wiring of the USB port. So they are in fact USB based. They're just hooked in from inside the computer instead of out of it. A lot of companies are considering running more than webcams off of USB in the future, in fact, some internal wifi cards are also soldered into the internal usb ports nowadays. We're probably about to go to computers which fully rely on them if you want the truth. I know my aunt recently purchased one which had EVERYTHING usb based (sound, keyboard, mouse, printer) they even have screens now which are usb based.

---

### Post by craig10x on 2012-04-20
Thanks...very interesting input :p
Here it is...hope this helps...

---

### Post by tmaranets on 2012-04-20
Does the reading "No Device found" in Skype? (if you have it)

---

### Post by tmaranets on 2012-04-20
In guvc, your webcam should pop up as some USB device. If it doesn't show up in device, I'm guessing your webcam connection is off internally.

---

### Post by craig10x on 2012-04-20
in guvc, a window pops up and says:  

unable to open device
please make sure camera is connected and the correct driver is installed

the actual program is unable to open up at all just that window comes up...

in cheese, the program opens but instead of the camera coming on and seeing the image, the image box is black and it says "no device found"

 regarding skype: i don't have it installed on here...

and if this means the webcam connection is turned off i wonder how i could get it to turn on?

---

### Post by ZekeGraal on 2012-04-20
What model is your laptop?

---

### Post by craig10x on 2012-04-20
> **ZekeGraal said:**
> What model is your laptop?

It's a Toshiba Satellite L770 series, which i purchased last July (2011) from Toshiba Direct...it wasn't a stock model it is custom built (where you select the particular components you want them to put in)...

It has an i3 core intel processor with intel graphics and 17.3" screen...

---

