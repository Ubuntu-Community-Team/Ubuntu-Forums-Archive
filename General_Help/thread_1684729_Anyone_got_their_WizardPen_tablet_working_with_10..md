---
title: "Anyone got their WizardPen tablet working with 10.10?"
date: 2011-02-09
forum: General Help
---

### Post by Noccy on 2011-02-09
The title has the question; has anyone got their WizardPen based tablets working with Ubuntu 10.10? I have delayed my upgrade as long as possible hoping that the support would come along but no matter what I try the cursor just sticks to the top left corner of the screen.

---

### Post by Favux on 2011-02-09
Sure.  We need to know what driver you need.  What does the tablet line in the output of:
```
lsusb
```
show?

---

### Post by Noccy on 2011-02-10
> **Favux said:**
> Sure.  We need to know what driver you need.  What does the tablet line in the output of:
```
lsusb
```
show?

lsusb lists it as:
```
Bus 005 Device 002: ID 5543:0004 UC-Logic Technology Corp. Genius MousePen 5x4 Tablet
```

xinput --list gives:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP5540U                 	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Gaming Keyboard                         	id=8	[slave  keyboard (3)]
    &#8627; Gaming Keyboard                         	id=9	[slave  keyboard (3)]
    &#8627; Logitech USB Receiver                   	id=10	[slave  keyboard (3)]
    &#8627; G15 Extra Keys                          	id=12	[slave  keyboard (3)]
```

---

### Post by Favux on 2011-02-10
That's a WizardPen tablet alright.  If the package in Maverick isn't working for you try the version in DoctorMo's PPA:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen](https://launchpad.net/~doctormo/+archive/xorg-wizardpen)

Should work, barring minor adjustments in the 70-wizardpen.conf.

---

### Post by Noccy on 2011-02-10
> **Favux said:**
> That's a WizardPen tablet alright.  If the package in Maverick isn't working for you try the version in DoctorMo's PPA:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen](https://launchpad.net/~doctormo/+archive/xorg-wizardpen)

Should work, barring minor adjustments in the 70-wizardpen.conf.

That is the version I am using. Is there any way to force a clean reinstall of it?

---

### Post by Favux on 2011-02-10
It's probably not the driver then but the match in the 70-wizardpen.conf.  Since you are in Maverick it should be in /usr/share/X11/xorg.conf.d/.  Let's see what it looks like.

---

### Post by Noccy on 2011-02-12
> **Favux said:**
> It's probably not the driver then but the match in the 70-wizardpen.conf.  Since you are in Maverick it should be in /usr/share/X11/xorg.conf.d/.  Let's see what it looks like.

I don't know why I didn't think of this earlier; the following solved the issues for me:

```
$ sudo apt-get remove --purge xserver-xorg-xinput-wizardpen
$ sudo apt-get install xserver-xorg-xinput-wizardpen
```

It now works perfectly again. Thank you :)

---

