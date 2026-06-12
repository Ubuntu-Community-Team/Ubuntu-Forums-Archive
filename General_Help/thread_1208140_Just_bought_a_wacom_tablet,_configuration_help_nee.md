---
title: "Just bought a wacom tablet, configuration help needed please"
date: 2009-07-08
forum: General Help
---

### Post by s3a on 2009-07-08
I bought the Wacom Bamboo MTE450K1 ([http://www.onhop.ca/Product/1298546?f=Pricegrabber](http://www.onhop.ca/Product/1298546?f=Pricegrabber)). I have the wacom-tools as well as xserver-xorg-input-wacom packages installed. I am using 64-bit. The digital pen has two buttons on it and they're both right clicks. There are four buttons on the actual tablet, two of which are left and right clicks and the third and fourth have no functionality at all.

What I want is:

- To improve the sensitivity of the pen because I have to cover so much surface area in order to move the cursor the slighest bit. Maybe it has to be this way but I would like to know where to go to experiment with this behaviour.

- To make one of the two buttons on the digital pen itself be a left click because that's what I'd need to be able to write. That, plus, there is no good reason as to why two buttons should have the same functionality on the same device.

- To assign a functionality to the two other buttons such as erasers and the toggling the typed text feature of xournal on and off.

I bought this product for school notetaking for the tasks that typing will not suffice such as math work, etc.

Any help would be GREATLY appreciated!
Thanks in advance!

---

### Post by Favux on 2009-07-08
Hi s3a,

Should be able to help you get set up.  But need to know what version of Ubuntu you are using.  It makes a difference.

---

### Post by s3a on 2009-07-09
Hi, I'll be honest with you...I am using Debian Lenny lol which is approximately between Ubuntu 8.04 and Ubuntu 8.10 in terms of how new it is. The reason for which I posted here along with the Debian and Linux forums is because Linux Wacom users are rare and I am desperate for help. Please don't avoid helping me because of this :( (I don't use Ubuntu and I still help out Ubuntu users - well, I use Ubuntu live CDs as well as flash drive installations but not on harddrive).
[I]
deniz@debian:~$ apt-cache search wacom
wacom-tools - utilities for Wacom tablet devices
xserver-xorg-input-wacom - X.Org X server -- Wacom input driver
deniz@debian:~$ apt-cache policy wacom-tools xserver-xorg-input-wacom
wacom-tools:
  Installed: 0.7.9.3-2
  Candidate: 0.7.9.3-2
  Version table:
 *** 0.7.9.3-2 0
        500 [http://ftp.ca.debian.org](http://ftp.ca.debian.org) lenny/main Packages
        100 /var/lib/dpkg/status
xserver-xorg-input-wacom:
  Installed: 0.7.9.3-2
  Candidate: 0.7.9.3-2
  Version table:
 *** 0.7.9.3-2 0
        500 [http://ftp.ca.debian.org](http://ftp.ca.debian.org) lenny/main Packages
        100 /var/lib/dpkg/status
deniz@debian:~$[/I]

My wacom bamboo tablet works just not the way I'd like it to! I want to configure buttons to have different functionalities and I'd like to change the sensitivity. I'm having difficulty writing with it even when I (temporarily) change the function of the button in xournal (not the tablet's own configuration) near my index for it to be a left click so that I can write. Could this be because my tablet is "behaving like a mouse" like I think I read on one of the millions of pages I've found using google? Or do I just need to adjust sensitivity?

Please help!

---

### Post by Favux on 2009-07-09
Hi s3a,

Ok, from what you are saying you are using xorg.conf.  Sounds like that's set up fine.  I can take a look at it if you want.

Your linuxwacom drivers are old, with 0.7.9.3 usb support had just been introduced.  I don't know if Debian Lenny will take a Ubuntu "deb" but consider going to Loic2's Wacom wiki and downloading the 0.8.1-6 deb.s there for your architecture:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)  They're near the top in the Intrepid section.

It sounds like you may not have calibrated and configured the tablet using "wacomcpl".  If so see more on using it in Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

Gemnoc in post #7 here:  [http://ubuntuforums.org/showthread.php?t=1098822](http://ubuntuforums.org/showthread.php?t=1098822)  shows one way to set up the pad.  Actually you could probably add those lines to your .xinitrc (the hidden file in /home/username/ that wacomcpl generates) if you wanted to.

Hope this helps.

---

### Post by s3a on 2009-07-10
I feel sooooo stupid, I spent soooo many hours just trying to make .deb files out of source code of anything which is why I took so long to answer here in a failed attempt to get Debian .debs and not ubuntu ones. Having failed miserably, I went to [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) like you suggested and installed the wacom-tools and xserver-xorg-input-wacom of Intrepid. I had to add the --force parameter for the xserver-xorg-input-wacom however I got it installed thanks to that.

Before installing these Ubuntu .deb files, the wacomcpl command launched absolutely nothing. Now, it launches something however under "Select the Device" no device appears.

---

### Post by Favux on 2009-07-10
Hi s3a,

Alright, sounds like the tablet is active and wacom-tools installed since you are seeing wacomcpl.  One thing you need to keep in mind is that the wacom driver (xserver-xorg-input-wacom) version and wacom-tool version have to be the same or things don't work and bad things can happen.  The same if there are remnants of a different version still around.

Are you configuring through a xorg.conf or a wacom.fdi?  Either way could I see it?

This should show you your wacom input devices:
```
xsetwacom list
```
Stylus, eraser, cursor (if you have the Wacom mouse), and pad.  If blank (which I expect since no devices in wacomcpl) try:
```
xinput --list
```
to see what's going on.

---

### Post by e24ohm on 2009-07-10
> **s3a said:**
> I bought the Wacom Bamboo MTE450K1 ([http://www.onhop.ca/Product/1298546?f=Pricegrabber](http://www.onhop.ca/Product/1298546?f=Pricegrabber)). I have the wacom-tools as well as xserver-xorg-input-wacom packages installed. I am using 64-bit. The digital pen has two buttons on it and they're both right clicks. There are four buttons on the actual tablet, two of which are left and right clicks and the third and fourth have no functionality at all.

What I want is:

- To improve the sensitivity of the pen because I have to cover so much surface area in order to move the cursor the slighest bit. Maybe it has to be this way but I would like to know where to go to experiment with this behaviour.

- To make one of the two buttons on the digital pen itself be a left click because that's what I'd need to be able to write. That, plus, there is no good reason as to why two buttons should have the same functionality on the same device.

- To assign a functionality to the two other buttons such as erasers and the toggling the typed text feature of xournal on and off.

I bought this product for school notetaking for the tasks that typing will not suffice such as math work, etc.

Any help would be GREATLY appreciated!
Thanks in advance!
Is that product used for drafting? It is neat.

---

### Post by s3a on 2009-07-10
deniz@debian:~$ xsetwacom list
deniz@debian:~$ xinput --list
bash: xinput: command not found
deniz@debian:~$ su
Password: 
debian:/home/deniz# xsetwacom list
debian:/home/deniz# xinput --list
bash: xinput: command not found
debian:/home/deniz# exit
deniz@debian:~$ 

e24ohm:
I think people use it to draw on gimp and stuff with their hands however, I'm planning to use it to take notes at school for the things I cannot type (such as cartesian graphs, etc) or just to do my homework on without wasting/losing paper. I'm planning to get it working with the program called xournal which is also in the Ubuntu repositories.

Favux:
Debian Squeeze has the exact same version as Ubuntu .deb files you told me to install (0.8.1.6). Do you think it would make a difference if I went and installed those? I feel it could make a difference but I'm just asking.

---

### Post by Favux on 2009-07-10
Hi s3a,

I'd definitely go with native deb.s if you have the choice.  Or we could try compiling linuxwacom if we have to.

Disappointing the x list commands don't work on Debian.

What kernel do you have?  Do you know the Xserver version?  Some problem posting xorg.conf or .fdi?

---

### Post by s3a on 2009-07-10
deniz@debian:~$ apt-cache policy wacom-tools xserver-xorg-input-wacom
wacom-tools:
  Installed: 0.8.1.6-1
  Candidate: 0.8.1.6-1
  Version table:
 *** 0.8.1.6-1 0
        100 /var/lib/dpkg/status
     0.7.9.3-2 0
        500 [http://ftp.ca.debian.org](http://ftp.ca.debian.org) lenny/main Packages
xserver-xorg-input-wacom:
  Installed: 0.8.1.6-1
  Candidate: 0.8.1.6-1
  Version table:
 *** 0.8.1.6-1 0
        100 /var/lib/dpkg/status
     0.7.9.3-2 0
        500 [http://ftp.ca.debian.org](http://ftp.ca.debian.org) lenny/main Packages
deniz@debian:~$ 

The above packages are from Squeeze. I also tried with Sid's but I've had the same issue which is that "wacomcpl" does absolutely nothing (command not found). However, it did with the Ubuntu .deb files you suggested earlier. This is weird, do you know why the same exact version across a distro is different? Now, I realize that my wacom tablet is acting like a mouse after loading the Ubuntu 9.04 live cd which detected everything out of the box and still isn't perfect but it is much better than my current situation and I did find the "floating sensitivity" like before it touches the tablet to be too sensitive and it made me angry lol. But now I understand how it is supposed to work because I thought I would have to keep a button pressed while I write which is pretty hard.

I am using the 2.6.29-bpo.2-amd64 kernel because the default Lenny kernel (2.6.26) does not support my built-in wireless internet card. Until the Lenny and a half kernel comes out, this will be the kernel that I'll be using (which I obtained from backports).

---

### Post by zoomy942 on 2009-07-10
trust Favux - he is a genius

---

### Post by s3a on 2009-07-10
deniz@debian:~$ apt-cache policy xserver-xorg
xserver-xorg:
  Installed: 1:7.3+19
  Candidate: 1:7.3+19
  Version table:
 *** 1:7.3+19 0
        500 [http://ftp.ca.debian.org](http://ftp.ca.debian.org) lenny/main Packages
        100 /var/lib/dpkg/status
deniz@debian:~$

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
EndSection

And there is no xorg.fdi in /etc/X11 if that is what you asked for.

(I forgot to add these in the previous post)

---

### Post by Favux on 2009-07-10
I wish!

Hi s3a,

On the Jaunty live CD what you're running into is the Jaunty 10-wacom.fdi isn't right, we've fixed it.

I assume the variations are do to whatever packaging choices the packager used.  Could that be why the X list commands aren't working?

With your kernel you could go the HAL route, if the infrastructure is in place.  I doubt it.

In Ubuntu the xorg.conf is in "/etc/X11/xorg.conf" and the 10-wacom.fdi is in "/usr/share/hal/fdi/policy/20thirdparty/".  I really need to see which you're using.  Then we can backtrack to see what we need to do with the drivers.

---

### Post by s3a on 2009-07-10
_11-x11-synaptics.fdi (obtained from Lenny installation through Ubuntu 9.04 Live CD not that it necessarily matters):_

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="AlpsPS/2 ALPS">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="appletouch">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
    </match>
  </device>
</deviceinfo>

---

### Post by Favux on 2009-07-10
Hi s3a,

Problem identified.  No wacom entries in xorg.conf.  This will take me a few minutes.  Did the Bamboo come with a Wacom mouse?

---

### Post by s3a on 2009-07-10
Oh so if it's an xorg.conf issue, then can I still use Lenny's wacom-tools and xserver-xorg-input-wacom packages instead of Squeeze's?

No mouse was included. I use my laptop's touchpad as my mouse. This is what I bought: [http://www.onhop.ca/Product/1298546?f=Pricegrabber](http://www.onhop.ca/Product/1298546?f=Pricegrabber)

---

### Post by Favux on 2009-07-10
Hi s3a,

OK here it is.

Now be sure to back up your xorg.conf and be prepared to restore it at a command line.  In addition to your newer kernel I'm guessing you have at least Xserver 1.6 because there is no "ServerLayout" in your xorg.conf.  The original xorg-xserver in Jaunty had a bug that caused X breakage when wacom entries were added to "ServerLayout".  Since I don't know what version you have...  Plus we may need to make the keyboard and mouse entries to "ServerLayout", I hope not.  Plus the video entries may have changed, so the ones I put in may cause problems.  I don't think so, but...  So install it and reboot.  Then see if wacomcpl works and the X list commands.

The lenny linuxwacom may work.  But like I mentioned it's pretty old for usb support.  Of course it may have been patched.  And since we're using the wacom symlinks for pci path I don't know if it's wacom.rules are up to date enough for a Bamboo.

---

### Post by s3a on 2009-07-10
Thank you sooooooooooooooooooooo much!!!!!! You have no idea how important this is to me!!!!!! I just blindly copy pasted what you added however, now I will work on understanding what I copy pasted. I also got it working with Lenny's version. Thanks again!

---

### Post by Favux on 2009-07-11
Hi s3a,

You're welcome.

If you look at the Wacom wiki:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)  You'll see there are links, one to xorg.conf entries:  [https://help.ubuntu.com/community/WacomTroubleshooting](https://help.ubuntu.com/community/WacomTroubleshooting)  And of course you can look at "man xorg.conf".

To understand what I meant about wacom symlinks and wacom.rules see near the end of Section 2 and Appendix 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  And to setup wacomcpl see Section 3 on the same HOW TO.

---

### Post by e24ohm on 2009-07-13
> **s3a said:**
> deniz@debian:~$ xsetwacom list
deniz@debian:~$ xinput --list
bash: xinput: command not found
deniz@debian:~$ su
Password: 
debian:/home/deniz# xsetwacom list
debian:/home/deniz# xinput --list
bash: xinput: command not found
debian:/home/deniz# exit
deniz@debian:~$ 

e24ohm:
I think people use it to draw on gimp and stuff with their hands however, I'm planning to use it to take notes at school for the things I cannot type (such as cartesian graphs, etc) or just to do my homework on without wasting/losing paper. I'm planning to get it working with the program called xournal which is also in the Ubuntu repositories.

Favux:
Debian Squeeze has the exact same version as Ubuntu .deb files you told me to install (0.8.1.6). Do you think it would make a difference if I went and installed those? I feel it could make a difference but I'm just asking.

hey let me know how it works out. I am a mechanical engineering student, and this looks very ideal.

cheers mate.

---

### Post by s3a on 2009-07-29
_e24ohm:_
Well to answer you: this digital pen is a godsend! I can't believe I didn't buy this earlier! I know I wouldn't be able to use it to take notes, etc at school but at least I could have used it instead of wasting scrap paper for math, physics, chemistry homework, etc. But now, I can use it in school and at home. And thanks to xournal I can relocate handwriting without erasing and rewriting like on paper, I can use multiple colours, I have ruler/highlighter as one of my button shortcuts and the other as my eraser shortcut. Not to mention, xournal can even open pdf exams for me to actually write on! So no more: a) Needing paper versions to write on. Or the alternative: b) look at a pdf using evince or something and then re-writing things on paper! Not to mention, there is a shape recognizer! And you can also type the stuff that is not math related! Cleary, you can see how happy this device made me and how it contributed to the rest of my joyful GNU/Linux experience. ;)

_Favux:_
deniz@debian:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
EndSection

[I]Section "InputDevice"
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "USB" "on" # USB ONLY
Option "Button2" "2"  # make first button a middle button
Option "Button3" "3"  # make second button a R button
EndSection

Section "InputDevice"
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "USB" "on" # USB ONLY
EndSection

Section "InputDevice"
Identifier "pad"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "pad"
Option "USB" "on" # USB ONLY
EndSection[/I]

Section "Device"
Identifier "Configured Video Device"
Driver "intel"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
[I][B]InputDevice "stylus" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
InputDevice "pad" # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
EndSection[/B][/I]
deniz@debian:~$

Ok so the parts of the xorg.conf that are important are the italic stuff but I was just wondering if the bold and italic part is important and if it is, what it does in comparison to the non-bold part. Could you explain please?

---

### Post by Favux on 2009-07-29
Hi s3a,

Glad your Wacom tablet is proving so useful.

The Wacom lines in "ServerLayout" are important.  They are what actually make the Wacom sections above "active".  If you comment them out you should find you lose tablet function, i.e. the Wacom sections are no longer active.  At least that has been true.

In Ubuntu because the xorg.conf is being deprecated some funny stuff is happening.  I've seen some people claim (partial?) activity without the "ServerLayout" lines in Jaunty, which by default doesn't have "ServerLayout" at all.

I hope this clarifies things.

---

### Post by s3a on 2009-07-29
Ok but, do they have to be on the absolute bottom of the xorg.conf file? Can they be right below the other wacom tablet stuff? The "funny stuff" is due to HAL, isn't it?

---

### Post by Favux on 2009-07-29
Hi s3a,

I've seen "ServerLayout" everywhere, but I think it's suppose to be at the bottom, or at least was at one point.  But if it works it works.

Yes HAL, the newer kernels (2.6.28 and up), and probably mostly due to the new Xserver 1.6.

---

### Post by duuchung on 2013-02-17
I just saw this old thread when I dug out my Tegaki thread. I have been trying to input Chinese characters into my beloved Ubuntu for almost a decade. The easiest way out for me is to use a handwriting tablet.

After some googling, I found that Wacom and a particular Asus Eee device were only user friendly to Linux. But Wacom is a little expensive costing around US$80 in HK. All along I used a XP to type Chinese.

My ubuntu is a virtualbox with XP. I just installed a US$3 tablet from Golden. It works in the virtual machine. The files are stored in VBShare at Vboxsrv. Finally I can input Chinese into my Ubuntu. Bingo!

My next mission is to buy a writing tablet for Red Flag Linux machine and try it in my Ubuntu.

---

### Post by howefield on 2013-02-17
Old thread closed.

---

