---
title: "Setting up Xvfb with firefox and selenium"
date: 2009-07-15
forum: General Help
---

### Post by mkotasek on 2009-07-15
Hello out there,

I am trying to setup Xvfb on a headless machine so I can run firefox and subsequently selenium for test automation.  I am not an expert in linux, so if I am missing something obvious, please point it out!

I so far have installed Xvfb through apt-get, firefox came natively on the system, and I have installed java and have the jar files necessary for selenium.  The first problem arises when I attempt to start a display using Xvfb.  I use the following command:

sudo Xvfb :99 -ac

The Output:

Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
(EE) config/hal: NewInputDeviceRequest failed
(EE) config/hal: NewInputDeviceRequest failed

I take it the font path element is just a warning and can be ignored, however the NewInputDeviceRequest failures are more worrisome.  At this point if I try to start firefox using the display defined, I receive an error:

satest@satest-desktop:~$ firefox --display:99
Xlib:  extension "RANDR" missing on display ":99.0".

I am not sure if it is related to the above or not.

I would greatly appreciate guidance in this situation.  I have been googling around and all I've gotten was more gray hair. :(

Thanks,
Max

---

### Post by FormerRedHatUser on 2009-10-08
[FONT="Arial"]Max,

I don't get the[/FONT] 

[INDENT][FONT="Fixedsys"](EE) config/hal: NewInputDeviceRequest failed[/FONT][/INDENT]

[FONT="Arial"]error, but I do get the[/FONT] 

[INDENT][FONT="Fixedsys"]Xlib:  extension "RANDR" missing on display ":99.0".[/FONT][/INDENT]

[FONT="Arial"]message.  I don't know what it means, but it doesn't affect the Selenium tests.[/FONT]

---

### Post by thisisvlad on 2010-09-17
> **mkotasek said:**
> Hello out there,

Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
(EE) config/hal: NewInputDeviceRequest failed
(EE) config/hal: NewInputDeviceRequest failed

Thanks,
Max


Max,

did you ever figure out a solution for this?  i am getting the same error.

*v

---

### Post by humpdebump# on 2010-12-15
> **thisisvlad said:**
> Max,

did you ever figure out a solution for this?  i am getting the same error.

*v

sudo apt-get install xfonts-cyrillic

---

