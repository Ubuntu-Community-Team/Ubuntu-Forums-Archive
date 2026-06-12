---
title: "HP Touchsmart Tm2 and Ubuntu: Workarounds, Solutions and Tips"
date: 2010-11-08
forum: General Help
---

### Post by Michael S Corigliano on 2010-11-08
This little guide is for anyone with an HP Touchsmart Tm2 series running Ubuntu 10.04 and above.

**PLEASE NOTE:** These workarounds, solutions, and tips have been tested and verified to work on an HP Touchsmart Tm2-2050us running Ubuntu 10.04 Lucid Lynx and Ubuntu 10.10 Maverick Meerkat.

**Installation:** There are no problems I have experienced with installation except for the display not working on the live USB/CD images occasionally, this can be fixed by simply closing the display lid, and reopening it (this usually has to be done at least 2 or 3 times).

**Display:** Most times after boot up, the display is black. A workaround for this is closing the lid and reopening it (repeat until the display works). Another reported solution is as follows:

1) Open a terminal
2) Type:
```
sudo nano /etc/rc.local
```
3) Add this to the bottom of the file (this disables the ATI part of the hybrid graphics card):
```
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```
4) Press CTRL-X (to exit), Y (to save changes), and ENTER/RETURN to accept the file name.
5) Reboot

*Note: This solution is also reported to increase battery life.*

**Trackpad:** It may seem that the right click button is disabled, but it isn't. To right click, you must tap the very bottom right corner of the trackpad. Also, by default the trackpad does not have multi-touch enabled (even though it is capable of it). A reported solution for this is:

1) Open a terminal
2) Type:
```
sudo nano /etc/X11/xorg.conf.d/50-two-finger-scroll-touchsmart-tm2.conf
```
3) Add this to the bottom of the file:
```
Section "InputClass"
   Identifier "enable synaptics SHMConfig" 
   MatchIsTouchpad "on"  
   MatchDevicePath "/dev/input/event*"
   Driver "synaptics"
   Option "SHMConfig" "on"
   Option "EmulateTwoFingerMinW" "5"
   Option "EmulateTwoFingerMinZ" "60"
   Option "VertTwoFingerScroll" "1"
   Option "HorizTwoFingerScroll" "1"
EndSection
```
4) Press CTRL-X (to exit), Y (to save changes), and ENTER/RETURN (to accept file name)
5) Reboot

*Note: if this workaround periodically stops working, then type these two commands into the terminal:*
```
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
```

**Touchscreen:** The touchscreen recognizes gestures fine out of the box, but they are a bit laggy and unresponsive at times. I suggest adding a repository and installing the a few packages (*kde-config-tablet* is only necessary if you run KDE). Open up a terminal and type the following:

1) ```
sudo add-apt-repository ppa:tkluck/ppa
```
2) ```
sudo apt-get update
```
3) ```
sudo apt-get install xserver-xorg-input-wacom wacomrotator kde-config-tablet
```
4) ```
 sudo apt-get update
```
5) ```
 sudo reboot 
```

**Digitizer Pen:** Surprisingly, there haven't been any problems that I have encountered with the pen. If you have any, please let me know.

**Sound Card:** The Intel HDA 5 Series/3400 sound card my model came with only has one audio jack (for both input and output). The output works perfectly fine for me, but when I open *alsa-mixer* via terminal and change "line-in" to "mic-in", it does not receive any signal. I have not come across a solution or workaround to this problem, but if you have, don't hesitate to share it with me and the community.

**HDMI:** Works, but no sound output.

**F-Keys/Action Keys:** By default, the action keys are only enabled. You can fix this by hitting ESC when the HP splash screen appears during boot up. Go to the BIOS and the option is in there. Disable the action keys (this will make if so you have your F-Keys, and action keys by pressing the "fn" key located to the left of the SUPER key (usually the key with a Windows logo on it).

**Front Mic**: You must unmute the microphone in "sound settings" for this to work.

**Page Up/Page Down Buttons Missing:** There are no page up and down buttons on this computer, but you can still use them. Press fn+the up arrow key for page up and fn+the down arrow key for page down.

**Wireless:** The Broadcom driver needed for wireless networking can be obtained by connecting to an ethernet connection, click "System" on the top GNOME panel, select "Administration" or whatever it says (I'm on KDE at the moment and cannot look), and then open "Additional Drivers"/"Restriced Drivers". Search for additional/restricted drivers, and install the Broadcom driver that will appear. Simple as that, you're wireless now :D.

**Fan:** Make sure the "ALWAYS ON" option is selected for the fan in the BIOS.


If you have any problems that were not listed here with or without a solution, please post in this thread. If you have any solutions/workarounds that were not listed, please also post. I take credit for none of these solutions but the opening and closing of the lid to fix the display.

**Sources:**
[http://www.infty.nl/wordpress/2010/10/ubuntu-on-hp-touchsmart-tm2/comment-page-1/#comment-10](http://www.infty.nl/wordpress/2010/10/ubuntu-on-hp-touchsmart-tm2/comment-page-1/#comment-10)

[http://www.murraytwins.com/blog/?p=65](http://www.murraytwins.com/blog/?p=65)

---

### Post by jan-90 on 2011-01-15
i dont know if im supposed to comment here but thanks i found this very useful.
im completly new to linux and after installing it about 6 times [many probs last of which nothing came up on the screen] i think i managed to have a learning ubuntu os setup
any updates would be great

---

### Post by Michael S Corigliano on 2011-01-25
No problem at all :). I suggest the KDE desktop for "tablet mode". Mainly for the Plasma Keyboard widget and such. To do that open a terminal and type in "sudo apt-get install kubuntu-desktop" (without the quotes of course). If you have an questions or problems, don't hesitate posting them here.

---

### Post by vedovatti on 2011-03-28
Hi there!I just submitted a bug report for the Finger print reader! bug # 744310 in launchpad.net. I hope you can collaborate! Cheers

---

### Post by android272 on 2011-04-15
does any one know how to get the side butten to work on the stylus(right click)

EDIT: you have to press the button and then tap the screen to right click

---

### Post by cemheren on 2011-05-22
I had a problem with X never starting in tm2, I was dropping to the tty console every time and found out that is was related to this bug [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/648631"). 

I blacklisted the INTEL_IPS as in above mentioned bug and the problem is solved.

I thought it might help to someone. 

best.

---

### Post by LiquidSolstice on 2011-06-13
Guys, I don't mean to resurrect a dead thread, but I've figured something out.

It's not that the screen won't turn on, it's that the backlight is off, and is unable to brighten back up again.

Try it yourself. When logged in (after doing the close lid/open trick) use the F2 key, and drop your brightness all the way until the screen is off.

Once it is, you'll find that pressing F3 doesn't bring it back. This is what we need to fix.

---

### Post by Sportingfan on 2011-07-02
This did the trick for me too. THANKS!

---

### Post by Albertoc67 on 2011-08-24
I've just followed the indications of Michael S. Corigliano and all seems right.
I turned off the laptop and then re-turned on and the display doesn't work.
I close and reopen the lid a lot of times but without result.:(
Please, can you help me?
Thanks a lot

---

### Post by leth on 2012-01-21
A tidbit of advice for anyone experiencing problems on the tm2; Update Your BIOS!

I have a tm2-1070ca with Intel-only graphics (not the hybrid ATI one) and struggled for a few weeks trying to get things working properly.  I could not boot unless I had the grub boot strings set to "nomodeset noapic noacpi vga=788" and whenever I closed the lid or my screen went to sleep it would not come back.  I was reading through bug reports regarding the graphics card and at the bottom of the comments someone mentioned an update to the HP BIOS.  I checked HP's website and sure enough I had an old version.  After updating the BIOS everything worked flawlessly except for two minor issues;

One was to do with the Synaptics trackpad where everything was double-clicking when I clicked once on the left trackpad button.  I forget which trick fixed it but I don't think it was the one posted here; I think it was just as simple as installing xserver-xorg-input-synaptics, but there might have been more to it than that (I was trying so many different fixes at the same time and wasn't keep notes.)

The other issue was to do with the brightness up/down buttons not working and the screen always staying at 100%.  The fix for this was here:

[http://ubuntuforums.org/showpost.php?p=9110804&postcount=94](http://ubuntuforums.org/showpost.php?p=9110804&postcount=94)

This trick has worked very well for me.

I am now happily running Ubuntu on my tm2 laptop.  The only hardware-related issue I have left it that Ubuntu will not boot when I have Virtualization Technology enabled in the BIOS.  I'm still working on figuring that one out but I wouldn't be surprised if it was a bug in the BIOS.

---

