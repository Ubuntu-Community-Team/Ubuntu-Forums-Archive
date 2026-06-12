---
title: "My keyboard and mouse will not work once I get to the login screen"
date: 2010-01-22
forum: General Help
---

### Post by NichB77 on 2010-01-22
I have a Logitech Wave keyboard and mouse for my computer. I am not sure which version of Ubuntu I am running on but I think it is 6.10. When I boot up my computer I can go into the BIOS and earlier today it would even let me press escape to seee which operating systems I could boot. Now it no longer lets me see the operating system I have (which is why I cant say which version of Ubuntu I have). It takes me to the log in page and asks for the username and password but I cant type and I cant move the mouse. Earlier I could also use Alt+F1-F12, but this is no longer working either so it just sits at the login page and nothing works at all. The computer that is having this problem is very old it is a Proteva and when I opened up the actual computer the processor says: 
 
ALI 
M1541 A1 
100 MHz 
9841 TS07 
XD229470000E 
Taiwan
 
At startup the computer says that the processor is a: AMD K-6
I know that the BIO's are to old for Ubuntu to run properly because at startup it also says that: "ACPI : BIOS age (1998 ) fails cutoff (2000), acpi=force is required to enable ACPI" it also says that: "ACPI : unable to load the System Description Tables."
I have'nt used this computer for about a year or two, but the last time I used it it worked perfectly fine. I have been seeing questions on the forums similar to mine, but their problems are on other versions of Ubuntu and their mouse's are said to work fine. I cant try any of the solutions for the problems I have read about because I cant open the prompt that you get when you are at the log in screen and press F2. I have no idea what to do. Does anybody know how I can fix this problem?

---

### Post by hwttdz on 2010-01-22
usb mouse and keyboard? If so it sounds like you need to enable something along the lines of "usb legacy keyboard support" and "usb legacy mouse support" in the bios.  Also if you have a ps2 (I think that's the name of the other connection), mouse/keyboard you can give that a go.  I don't understand the naming (I prefer usb to the other one), also there are ps2 to usb converters (i.e. plug usb mouse into ps2 port on board).  Let us know if that helps. 

On a somewhat unrelated note I'm excited to give bluetooth mouse/keyboard a try in the next week or so.

---

### Post by NichB77 on 2010-01-23
Yes it is a usb kkeyboard and mouse. II have looked in the BIO's and cant find anythiing called "usb legacy keyboard support" or "usb legacy mouse support". I have a PS2 mouse and have tried that before and had the same results.

---

