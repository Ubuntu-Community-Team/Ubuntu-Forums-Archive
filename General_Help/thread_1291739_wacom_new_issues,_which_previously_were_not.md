---
title: "wacom new issues, which previously were not"
date: 2009-10-15
forum: General Help
---

### Post by lalamax3d on 2009-10-15
upon installing ubuntu, i used to do three steps and it always worked
1- install wacom-tools from synaptic
2- download wacomproject
3- if running (wacomcpl) doesn't show device, i used to create a script (/etc/init.d/wacomtohal)
```
## find any wacom devices
for udi in `hal-find-by-property –key input.x11_driver –string wacom`
do
type=`hal-get-property –udi $udi –key input.x11_options.Type`
## rewrite the names that the Xserver will use
hal-set-property –udi $udi –key info.product –string $type
done
```
4- now wacomcpl, always show device and i used to configure easily.

this time. i did same. not sure that may be some kernel had been updated or what went wrong. but whatever i do, my device is not listed in wacomcpl GUI.
also noticed while searching other threads, some ppl do manual enter few lines in their xorg.conf. just wanted to know other thoughts.

also what is best way to check or remove wacomproject, which i had installed multiversions. now i wanted to remove all. this is because, first i downloaded latest version(0.8.4.3) it gave some error on (./configure) then i tried one previous , it apparently worked find(no errors)
what is best way to remove all of those, so that ubuntu doesn't know anything about those. 
can i assume that i downloaded (tar.bz) files on desktop, extract them there and run ./configure in extracted folder. >> now removing that folder means, i have removed app / driver or linux has put it somewhere else.???

---

### Post by Favux on 2009-10-15
Hi lalamax3d,

Are you still using Jaunty?  Or are you now using Karmic beta?

Which tablet do you have?  Is it a serial tablet?

To remove compiled and installed linuxwacom please see Appendix 4 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

What was the error on ./configure with 0.8.4-3?

---

### Post by lalamax3d on 2009-10-15
> **Favux said:**
> Are you still using Jaunty?  Or are you now using Karmic beta?

using ubuntu / kubuntu 9.04(x64)
intous 3, 12 inch  tablet

linuxwacom (0.8.4) error:
```
No package 'xorg-server' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```
now going to read appendex 4 to remove and then replying you in a second. thanks for taking time and helping me out, extremely greatful

---

### Post by lalamax3d on 2009-10-15
i think i have uninstalled everything successfully, which was initial purpose of this thread. now point comes again about installing from scratch.
i have seen the link u post. contains detail information but i think its for too latest versions "karmic" sounds new.
if there is anything else, u would like to guide, please let me know here

---

### Post by lalamax3d on 2009-10-15
after restarting, i typed word "wacom" in synaptic search bar, it showed me two thing,
1- wacom-tools
2- xorg-server-wacom(something like that)
i added both and apply, restart
my tablet is working, i can move pen and cursor moves, i open gimp and pressure senstivity is working as well.

NOTE: i wanted to map one screen to tablet rather than two. but going to terminal and typing "wacomcpl" gives error, it says you can install this by typing "sudo apt-get install wacom-tools" but trust me: synaptic is showing this added (green box on left" i again added it via terminal as explained, it added but running it still gives same command
now i m extremely confused, because its useless without proper mapping
should i install linux wacom drivers >> which version and how (8.x.x) why wacomcpl is not working??

lastly, i just checked xorg.conf.. its amazing. no wacom entry in whole file. but its working
ahhhhh, i hate when i can't pin ponit root cause / error
someone please help

---

### Post by lalamax3d on 2009-10-15
i have purged wacom-tools and reinstall. its working, like intuos , useless right now
which means, wacomcpl working and open GUI but not showing anything
which also means, device is technically working but not useable, as i m not able to map screen1 to it. can't set / customize anything
also, no wacom entry in xorg.conf but device is still working...
please let me know if u know how to fix this??

---

### Post by Favux on 2009-10-15
Hi lalamax3d,

In Jaunty you use HAL/.fdi not the xorg.conf.  Post #176 explains this and has a .fdi to fix the 'xsetwacom list' being empty, no wacomcpl problem:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

Dual monitors is another issue.

---

### Post by Favux on 2009-10-15
Hi lalamax3d,


I'm sorry, if your Intuous 3 is a serial tablet ignore the above post.  That's only for usb tablets.  Your Intuous 3 is a serial tablet, correct?  We haven't establish if it is serial or usb yet.

If it is serial let's see what:
```
xinput --list
```
is calling your Wacom devices.

---

### Post by lalamax3d on 2009-10-16
ok, please, mine intous is USB.
i followed your post 176. it helped too much, because i copied, replace / overright,
reboot
check both commands return goodstuff and wacomcpl is working showing list
its amazing, i can't understsand what u have written in that magical fdi file but its amazing and it works.
also from now on, you can say it works with ubuntu and kubuntu
also it works with 32bit and 64bit versions, as i m using kubuntu 64bit

huge thanks for your patience and consistancy. ubuntu is gonna beat others because of helpful ppl like you in community, keep rocking
cheers, have a good day
regards, lala

---

### Post by bogdanbiv on 2009-10-16
Hello, I have problems with my USB tablet too. It's a Wacom Bamboo Fun with just a stylus (2 buttons stylus) and no other buttons on the tablet.

So if the stylus and stylus buttons work, then everything works.

However, despite the statement that the stylus should work out of the box, it doesn't. My xinput --list does not return any wacom device as is xsetwacom. If it wasn't for the:
```
$ lsusb | grep -i wacom
Bus 006 Device 002: ID 056a:00d4 Wacom Co., Ltd
```

I would think there is a hardware problem. I have tried several wacom.fdi files but none have worked so far.

I have installed the software: 
```
$ sudo apt-get install wacom-tools xserver-xorg-input-wacom
[sudo] password for bogdanbiv:
Reading package lists... Done
Building dependency tree
Reading state information... Done
wacom-tools is already the newest version.
xserver-xorg-input-wacom is already the newest version.
xserver-xorg-input-wacom set to manually installed.
```

The Wacom kernel module doesn't load automagically at boot, but with a little help from modprobe, it does:
```
$ lsmod | grep -i wacom
$ sudo modprobe wacom
$ lsmod | grep -i wacom
wacom                  25992  0
```

What else do I need to know/do? First I'd like to know how to find the device's name.

---

### Post by lalamax3d on 2009-10-16
hi bogdandiv,
not sure, about how to help you but hopefully favux will soon, generally speaking

try finding "gnome-device-manager" in synaptic, it shows devices connected to computer, simply run from applications>>system>>device manager

i agree, about xinput and xsetwacom difference in output but doesn't matter, first one shows info in detail, second one shows four lines just names.

---

### Post by Favux on 2009-10-16
Hi lalamax3d,

You are welcome.  Thank you for the nice words.  Glad you are setup.


Hi bogdanbiv,

Right now your tablet (Product ID 00d4) is not supported by linuxwacom.  We are trying to add it to linuxwacom on this thread:  [http://ubuntuforums.org/showthread.php?t=1290251](http://ubuntuforums.org/showthread.php?t=1290251)  We almost have it working.

The Wacom module does not load automatically on some systems.  To fix it add "wacom" (without the quotes) to the bottom of the 'modules' file in "/etc/".  In other words it's at "/etc/modules"

By the way the Vendor ID is 056a.

---

### Post by bogdanbiv on 2009-10-17
I'll see if I can help with testing.

> **Favux said:**
> Right now your tablet (Product ID 00d4) is not supported by linuxwacom.  We are trying to add it to linuxwacom on this thread:  [http://ubuntuforums.org/showthread.php?t=1290251](http://ubuntuforums.org/showthread.php?t=1290251)  We almost have it working.

---

### Post by samoyed on 2009-11-21
Hello everybody,

Iam totally new to linux, after reading lots of posts ,I some how managed to work on ubuntu 9.10, I have wacom Intuos 3 ,model PTZ-630, I tried to install driver from synaptic package manager, and installed wacom-tools & xserver-xorg-input-wacom, but when I type in terminal wacomcpl  a blank window popup and it does't show wacom device .i have attached the xinput list display, I have read several post and the the post by Favux , Iam really confused where to start  , how and what to do , In windows it was very easy to configure my tablet , but in ubuntu iam totally lost , I hope everybody can understand my situation , Kindly guide me .

Thanks n regards

---

### Post by Favux on 2009-11-21
Hi samoyed,

If you can run "xinput --list" in a terminal and attach the results I'm sure you can do the rest.  Your Intuos 3 is usb, correct?

What xinput shows is that HAL is calling:

stylus = "Wacom Intuos3 6x8"

eraser = "Wacom Intuos3 6x8 eraser"

And similarly for cursor and pad.

So if you run "xsetwacom list" in a terminal it will be blank and that is why wacomcpl won't work.  You need a new wacom.fdi that will parse (translate) the HAL names correctly into stylus, eraser, cursor, and pad.  So install the modified wacom.fdi in [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").  Just follow the instructions.  Ask if you have questions.

---

### Post by samoyed on 2009-11-21
Thanks, 
Favux  for quick reply, ya my wacom is usb , and xsetwacom list doesn't give me anything, like it doesn't run,  ok now i will check the post which you said and try if I had some difficulties I will post .

Thanks n regards

---

### Post by samoyed on 2009-11-21
Thanks a lot, Favux,

I have done according to your post# 176 , now everything works !
thanks for the guidance.

regards

---

### Post by Favux on 2009-11-21
Hi samoyed,

You're welcome.  Great, you are all set up now!

---

