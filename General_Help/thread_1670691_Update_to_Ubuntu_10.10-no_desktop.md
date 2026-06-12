---
title: "Update to Ubuntu 10.10-no desktop"
date: 2011-01-19
forum: General Help
---

### Post by David Crockett on 2011-01-19
Hi all,

I have just updated my deskop, an IBM Intellistation M Pro with Ubuntu 10.10.    After following all of the instructions and restarting the computer it comes up in terminal mode.   

How can I get it to go to the desktop.

Version 10.04 worked great and the update on my laptop, which I am using now is good.

Regards,
DC

---

### Post by mastablasta on 2011-01-19
what graphics card do you have? did you use any proprietary drivers for it? if so they would have to be removed before upragding.

---

### Post by David Crockett on 2011-01-19
I am using a nVidia card.   Which one I do not remember.     And yes I do believe that it was a proprietary driver.   

I did not remove it.  I had no idea that I need to do so.   So what do i do now.

DC

---

### Post by David Crockett on 2011-01-19
HI,

I have tied the following commands.

After reboot I log in

then:   sudo cd /etc/X11

it asks for my sudo password--I give it and I get the following error message:

cd: cmand not found.   

What's wrong.

DC

---

### Post by ajgreeny on 2011-01-19
You can't use ```
sudo cd /path
```just ```
cd /path
``` will change dirtectory, then you can use **sudo** to give root permissions to do what you want.

What is it that you are trying to do anyway, with that command, edit the xorg.conf?  If so use ```
gksudo gedit /etc/X11/xorg.conf
``` but backup first just in case with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conbak 
```

---

### Post by David Crockett on 2011-01-19
Ok my problem is that the config file will not allow me to have launch the desktop.

I  did not know that I had disable the proprietary driver for the video card prior to updating to 10.10.     I tried following the Ubuntu online manual--

In the manual ti tells you to use the use the command:  service dgm stop (which seems to work ok and then do sudo X -configure.

it fails to do it saying that the new of screens do not match and a few other errors and it does not generate the xorg.conf_new that manual hints that it should.

I am at a loss as to where to go form here.     

DC

---

### Post by ajgreeny on 2011-01-19
At the login screen try using failsafe gnome from the session menu, bottom right after choosing username.  That may get you to a low resolution desktop with the vesa driver, and from there you may be able to use the GUI to get a new nvidia driver for your card using the **System->Administration->Hardware drivers** menu item (now renamed I think to Alternative drivers).

Then logout and back in again to gnome this time, not failsafe gnome.

---

### Post by David Crockett on 2011-01-19
Hi,

 When the computer turns on it comes up in terminal mode:

Ubuntu 101.10 Cuneatus tty1    (Cuneatus is the computer's name)

Cuneatus logon:

After loging on it seems perfectly happy in the terminal mode, does not report any errors.

Regards,
DC

---

### Post by David Crockett on 2011-01-19
Hi,

 When the computer turns on it comes up in terminal mode:

Ubuntu 101.10 Cuneatus tty1    (Cuneatus is the computer's name)

Cuneatus logon:

After loging on it seems perfectly happy in the terminal mode, does not report any errors.

Regards,
DC

---

### Post by David Crockett on 2011-01-19
When the computer turns on it comes up in terminal mode:

Ubuntu 101.10 Cuneatus tty1    (Cuneatus is the computer's name)

Cuneatus logon:

After loging on it seems perfectly happy in the terminal mode, does not report any errors.

Regards,
DC

---

### Post by David Crockett on 2011-01-19
When the computer turns on it comes up in terminal mode:

Ubuntu 101.10 Cuneatus tty1    (Cuneatus is the computer's name)

Cuneatus logon:

After loging on it seems perfectly happy in the terminal mode, does not report any errors.

Regards,
DC

---

### Post by Splat_NJ on 2011-01-19
If my kernel gets updated I usually need to log in and do an "aticonfig --initial" for my ATI card.  Recreate your xconf.org file or simply reinstall your video drivers via command line.

---

### Post by David Crockett on 2011-01-21
Thank you for your information.   I in the end downloaded Ubuntu 10.10 on CD and stared over.    And now the system work great except for the fact that there is no sound.   I had no sound under 10.04 either.  I am sill working on that.

It does detect my sound card, but it does not seem to work.

Regards,
DC

---

