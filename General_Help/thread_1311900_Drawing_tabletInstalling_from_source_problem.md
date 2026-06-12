---
title: "Drawing tablet/Installing from source problem"
date: 2009-11-02
forum: General Help
---

### Post by user333 on 2009-11-02
I got a medion (made by waltop) drawing tablet last year. It worked fine on XP and ubuntu, but now it won't work on ubuntu anymore. :( Before ubuntu didn't need any drivers to work, but after I upgraded to 9.10, (which I am very happy with;)) the pen reads and moves the cursor... but it won't click (I need it to click, or else it won't do me any good). I downloaded the drivers from the waltop site for windows and linux, but I can't compile the linux one. First is says to type "./config". When I do that, it either says there is no such command or there is an errror. Then the readme says to run the "configure" script. That always goes OK. Then I am supposed to type "make". It prints out buch of lines, the last one saying : "error 2" Then I try running the install-sh script. All it says then is "no input file selected". I have this problem with a lot of programs and drivers.

Any help for either of these problem would be very helpful.

---

### Post by Giblet5 on 2009-11-02
Tell me what you downloaded and from where. I'll build it and explain what needs to be done to build it at your end.

Are you sure you can't use the Wacom or Aiptek drivers?


Or don't.

---

### Post by user333 on 2009-11-02
No, I don't think other drivers would work.

Here is the link to the site:

[http://www.waltop.com/download.asp?lv=0&id=2](http://www.waltop.com/download.asp?lv=0&id=2)

There should be only one Linux driver, second from the bottom. Thanks for offering to help :D
(I don't know if I have all the packages I need to compile it either, so could you tell me what I 
should have?)

---

### Post by tudor117 on 2009-11-02
Hi,
Just out of interest, I have a Genius tablet (waltop rebranded) and I've used the wizardpen drivers and then the wacom drivers.
You should give the wizardpen drivers a try as they were not to bad for me. However, waltop is the way to go. The ubuntu devs did something and the waltop drivers don't work momentarily in Karmic.
[Here]("http://ubuntuforums.org/showthread.php?t=1261407&page=7"), we're trying to get it to work again. Best of luck.

---

### Post by user333 on 2009-11-03
Thanks but..... what do I do? I really like this drawing pad. I found out my system calls it "slim tablet". The wizzardpen drivers didn't work, even though the terminal detected my pad. :confused:
I would be very happy if someone could help me.
 I am having big problems installing the drivers. When I try to "make", I get this:


> .....wizardpen.c: In function 'DeviceInit':
wizardpen.c:648: warning: passing argument 3 of 'InitValuatorClassDeviceStruct' makes integer from pointer without a cast
/usr/include/xorg/input.h:281: note: expected 'int' but argument is of type 'int (*)(struct _DeviceIntRec *, struct xTimecoord *, long unsigned int,  long unsigned int,  struct _Screen *, BOOL)'
wizardpen.c:648: error: too many arguments to function 'InitValuatorClassDeviceStruct'
make[1]: *** [wizardpen.lo] Error 1
make[1]: Leaving directory `/home/user333/wizardpen-0.6.0.2/src'
make: *** [install-recursive] Error 1......I just can't compile the wizzardpen source, and the .deb doesn't work either. In fact, I can't compile ANYTHING!!! Don't know why though. :(

---

### Post by tudor117 on 2009-11-06
Hi user333,

try this: [http://ubuntuforums.org/showpost.php?p=8244394&postcount=95](http://ubuntuforums.org/showpost.php?p=8244394&postcount=95)

---

### Post by drpjkurian on 2009-11-26
> **user333 said:**
> Thanks but..... what do I do? I really like this drawing pad. I found out my system calls it "slim tablet". The wizzardpen drivers didn't work, even though the terminal detected my pad. :confused:
I would be very happy if someone could help me.
 I am having big problems installing the drivers. When I try to "make", I get this:


I just can't compile the wizzardpen source, and the .deb doesn't work either. In fact, I can't compile ANYTHING!!! Don't know why though. :(

Hi
Please visit my thread

[http://ubuntuforums.org/search.php?searchid=67415926](http://ubuntuforums.org/search.php?searchid=67415926)

---

