---
title: "genius pensketch 9x12 } three years later and still not working"
date: 2011-03-19
forum: General Help
---

### Post by BcRich on 2011-03-19
hi 
I've had this genuis pensketch tablet for more then three years and have over the years tried just about everything to get it to work on the various versions of ubuntu. but have never suceeded. I've treid everything on this how to several times on several different versions of ubuntu [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)
but it never works
I once tried the particular pensketch i'm referring to on a MSwin machine and it worked perfectly, so I don't think there is a problem with the hardware. I must be configuring something wrong?
currently using 10.04 and 9.04 (would luv to have it working on both)

---

### Post by Favux on 2011-03-19
Hi BcRich,

Let's see what model it is.  We want to look at the outputs of the following commands entered in a terminal:
```
lsusb
```
(especially the line with the tablet)
```
xinput list
```

---

### Post by BcRich on 2011-03-19
Hi 
```
Bus 004 Device 002: ID 5543:0042 UC-Logic Technology Corp. Genius PenSketch 12x9 Tablet
```and 
```
"    Tablet PF1209"    id=5    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1

```This is in 9.04, Thanks!

---

### Post by Favux on 2011-03-19
Let's start with Lucid rather than Jaunty.  The UC-LOGIC tablet requires the WizardPen driver.  Jaunty isn't supported anymore and I'd have to think about how we set up WizardPen tablets in it.

So in Lucid show me the whole *xinput list*.  Then check in Synaptic Package Manager or the Software Center that the WizardPen driver is installed.  The package is something like xorg-xserver-input-wizardpen.

---

### Post by BcRich on 2011-03-22
hi 
r u still there?
sorry for the delay. after editing system files as instructions per this how to [https://wiki.ubuntu.com/TabletSetupWizardpen](https://wiki.ubuntu.com/TabletSetupWizardpen)
i was unable to boot into ubuntu 10.04. changed everything back to the way it was...
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Wireless Optical Mouse® 1.0A    id=9    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=11    [slave  pointer  (2)]
&#9116;   &#8627;     Tablet PF1209                           id=12    [slave  pointer  (2)]
&#9116;   &#8627;     Tablet PF1209                           id=13    [slave  pointer  (2)]
&#9116;   &#8627;     Tablet PF1209                           id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; PWC snapshot button                         id=8    [slave  keyboard (3)]
    &#8627; Logitech USB Receiver                       id=10    [slave  keyboard (3)]

```

---

### Post by Favux on 2011-03-22
Hi BcRich,

Hmmm.  Where did you get the WizardPen driver from and is it still installed?

We probably have to modify the 70-wizardpen.conf because although you have a UC-LOGIC tablet it is identifying itself as a "UC-Logic" or "Tablet PF1209".  So we'll have to use different keywords for the match.

---

### Post by BcRich on 2011-03-23
Hi Favux
Thanks for the reply! 
I got the driver from Martin Owens (DoctorMO)'s ppa [http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu](http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu). the name of the package is xserver-xorg-input-wizardpen.
If you are able to assist me with making the modifications to the 70-wizardpen.conf file I'm more than willing to take on that opportunity? here is what the 70-wizardpen.conf file looks like. Could this line ```
MatchDevicePath "/dev/input/event*"
``` and this line```
 MatchDevicePath "/dev/input/mouse*"
``` be the problem?
```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver "wizardpen"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/mouse*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSection
```Thanks most sincerely if you are able to help!

---

### Post by BcRich on 2011-03-23
I can hardly believe it, after following the instructions on this post [http://ubuntuforums.org/showpost.php?p=9252390&postcount=1](http://ubuntuforums.org/showpost.php?p=9252390&postcount=1) I finally have my pensketch working!!!!!
AWESOME! :D
my 70-wizardpen.conf file looks like this
```
Section "InputClass"
   Identifier "wizardpen"
   MatchDevicePath "/dev/input/event*"
   MatchProduct "Tablet PF1209"
    Driver        "wizardpen"
    Option        "TopX"        "721"
    Option        "TopY"        "1822"
    Option        "BottomX"    "32611"
    Option        "BottomY"    "32528"
EndSection

```
So happy right now :) thanks for the help Favux and al.do

---

