---
title: "Skype upgrade loses handset ..."
date: 2009-12-19
forum: General Help
---

### Post by Bucky Ball on 2009-12-19
hi all.

Odd one. I have a USB handset which i use for Skype. Updated Skype and now in 'options->sound devices' there is not c-port handset .... which was showing up fine in the superceded (old) version. (And that, of course, was how it showed in the last version).

In a terminal i input lsusb and the hand set shows up as c-port handset as per normal!

Before the upgrade, everything worked fine but after the upgrade the handset is not recognised by Skype. Reason for upgrade? Old version didn't give us SMS option and wife and I need that at the moment...

Any ideas? All welcome ....

---

### Post by Bucky Ball on 2009-12-19
In Skype, Options->Sound Devices, for sound in and out and ringing I get 'Pulse Audio Server (local)' and no other options to select. In the previous version the C-Port handset showed up no probs and I could select. 

Desperately need to fix this as we have no landline and have been using solely Skype for about five years so all and any suggestions, ideas, clues, stabs in the dark(!) welcome. ;)

---

### Post by Bucky Ball on 2009-12-20
Removed the new version of Skype and then attempted to reinstall it and I get this:

```
anna@Lounge:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package skype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package skype has no installation candidate
``` ... when I attempt to install through Synaptics I get the attached screenshot ... but that is a distraction. I can install from the .deb I downloaded easily enough.

It is obvious that the new version of Skype uses the Pulse Audio Server and that only. There is no C-Media C-port USB handset available in there nor anything else. I have twiddled and tweaked for a few hours now and gotten pretty much nowhere. Can anyone let me know if there is any way of re-installing the older version so I can get back to where I was? I cannot find any online. I even tried the Debian version but unmet dependencies. Help! We really need this phone to be working. ;(

---

### Post by Bucky Ball on 2009-12-20
Okay, have found an older version but still not working. Skype ver. 2.0.0.72. See the screenshot. I have it setup as it was before updating but the odd thing ... still not working. Wondering if I might have changed something which has now broken the old Skype setup as even though the handset shows up it is totally dead. I know it is working because Ubuntu gives me a tune through the handset when I plug it in ...

Strange that I can make a test call and I get no audio capture or playback errors and works fine so it seems to be having no problem with the C-Media USB handset (as it hasn't for years!), just the handset itself is dead(???). Maybe I have somehow switched it off in the sound settings.

---

### Post by Bucky Ball on 2009-12-20
Solved, in as much as I have a working version of Skype again but it hasn't really fixed my original problem which was getting the new version of Skype to work with my handset in Hardy. I have found a fix for just that for Intrepid and also this comprehensive HOWTO if your having problems with PulseAudio generally:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I unclicked 'Allow Skype to Manage Sound Settings' in Options->Sound Devices and the handset worked straight away. So, have a working version again but with no SMS which was the reason we were upgrading to 2.1 version. I'm going to install the newer version again and experiment and will post if I get anywhere.

---

