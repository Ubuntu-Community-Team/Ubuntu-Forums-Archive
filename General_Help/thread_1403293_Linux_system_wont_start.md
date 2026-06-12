---
title: "Linux system wont start"
date: 2010-02-10
forum: General Help
---

### Post by hyburn on 2010-02-10
hi folks,

I am having trouble getting my linux to start. I am posting this from my crappy windows machine.

ok here is how the story goes. I booted my linux, and did the update process. it told me that I needed to restart, so I did. now it wont boot. Please help me I have alot of personal data on my linux that i regretfully didnt back up.

-drew

---

### Post by audiomick on 2010-02-10
Hallo.
Firstly, don't panic about your data (yet....;) ).  As a last resort, you can copy it off using the live CD if you have to.

As far as the boot problem goes, give us a bit more info please.
When you try to boot, what do you get exactly?

---

### Post by hyburn on 2010-02-10
it will show the grub countdown.

then I get the ubuntu loading bar... as standard.

but then the screen goes blank. and doesnt load the login screen

---

### Post by hyburn on 2010-02-10
I'd like to state that I dont think its my video card, as it is brand new

---

### Post by audiomick on 2010-02-10
I don't think your video card would be the problem, but the driver might have got messed up in the update, maybe.
Try booting into recovery mode
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
firstly to see if it will boot at all, and secondly to see if you can't re-install the video driver there. I can't help you with that really, I've never had to do it.
As the linked page states, the recovery mode is command line only, so if you are not used to doing things in the terminal, that probably wont be much help to you either.

---

### Post by hyburn on 2010-02-10
thanks mic, im in, now its something with my video. its really shotty. I hope its showing you how bad this is.

it is still asking me for a restart, how do I undo the damage from the update?

---

### Post by hyburn on 2010-02-10
mic if you need info of my system to help me fix this, please just ask

---

### Post by audiomick on 2010-02-10
Hi.
Don't know if I can be much help actually, but what is your video card?

---

### Post by hyburn on 2010-02-10
ATI radeon XFX HD 4850

---

### Post by audiomick on 2010-02-10
oops, I am using nVidia....

I would look in system> administration> hardware drivers and make sure the proprietary driver is still enabled, _maybe _even disable and re-enable it and/or run the screen setup utiliity and make sure the settings are alright.

Also, try a forum search using the model of the video card as a search criterion.

I know that is not much help, sorry...

---

### Post by hyburn on 2010-02-10
I need to reinstall the driver, I'll just go threw my old posts and find the one where I fixed it last time. thanks again for your help mic

---

### Post by hyburn on 2010-02-10
no dice, on the restart, we are back to square 1

---

### Post by hyburn on 2010-02-10
OK im back in my linux, Im still trying to re-install the video driver, ,but im having trouble I did what was on this page
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#1._Install_necessary_build_tools_and_libraries]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#1._Install_necessary_build_tools_and_libraries")

but when I get to the end of the "do it the Ubuntu way. I told I can test it. with flgrxinfo. and this is my response

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14

what do I do?

---

### Post by hyburn on 2010-02-10
ok its working. I just needed to reinstall the video driver as I stated before. im going to do a restart. lets see what happens

---

### Post by hyburn on 2010-02-10
Boo ****** yeah, its workin. Thanks again for the help mic. Peace out folks

---

