---
title: "hp tx2 touchscreen click problem"
date: 2010-04-29
forum: General Help
---

### Post by eNoVa on 2010-04-29
Hey Guys,
Since I've installed lucid, I'm not able to trigger a click with my touchscreen anymore.
Additionally, i can't change the button-map of my n-trig Pen correctly because button 1 equals to the second button of my pen(i would like to have right click).
I guess something on the xorg.conf has to be changed - has someone advice?
greez
ps: on beta 2 everything worked

---

### Post by Favux on 2010-04-29
Hi eNoVa,

Welcome to Ubuntu Forums!

Try Rafi Rubin's new 10-wacom.conf N-trig snippet in xorg.conf.d.  This is described in Section 2 c) "Lucid-configuring through 10-wacom.conf" in the [linuxwacom HOw TO]("http://ubuntuforums.org/showthread.php?t=1038949&page=87").

Hope this helps.

---

### Post by dranorter on 2010-05-02
Hi,

I just did a fresh install too. It appears the relevant difference between that 10-wacom.conf and the default one was the line

Option "Button2" "3"

which got the right-click on the digitizer pen button working. But touching the screen still doesn't click.

To be clear, the digitizer can click but not the capacitive touch screen.

---

### Post by Favux on 2010-05-02
Hi dranorter,

As you probably know touch depends on a lot of things.  The firmware version you are using, the linuxwacom or xf86-input-wacom version, whether you are using evdev for touch, and which version of hid-ntrig.c/ko you have.  Right now Ayuthia is thinking things configure better through xorg.conf rather than xorg.conf.d.  See the last couple pages of the [N-trig HOW TO thread]("http://ubuntuforums.org/showthread.php?t=1252492").  You may want to post there.

---

### Post by dranorter on 2010-05-03
Well sorry for perpetuating this thread then I suppose. But as of right now my setup is a totally fresh 10.04 install.

But I must add, I was using the old (Vista) firmware when I reported the problem clicking, and updating the firmware in Windows 7 (with HP's 'upgrade manager' disc) fixed it -- in a manner of speaking. Now a light touch (low finger surface area) moves the pointer without clicking, and a press (higher finger surface area, or thumb) clicks. Ubuntu seems to be taking better advantage of the Windows 7/newer firmware in this respect than Windows 7 itself: in Windows, I have some trouble clicking without using my thumb, and the 'move without clicking' behavior is replaced with total lack of response.

Interesting, no? Sorry for not keeping up with the official threads and whatnot, right now my focus is on getting Windows running smoothly, not Ubuntu. :)

---

### Post by Favux on 2010-05-03
Hi dranorter,

No reason to apologize.  Thanks for letting us know a firmware update "fixed" things.  Which version?  And Rafi and Stephane would no doubt be flattered to hear their work on the hid-ntrig.c/ko compared so favorably to the Windows version.

---

### Post by dranorter on 2010-05-04
Firmware version 4.4.26.8.5.

I managed to find a 'recalibrate' option in the Windows 7 N-trig settings, so it now accepts clicks with smaller surface area. Hopefully that doesn't mean Ubuntu's behavior will change too. (I don't know if that's possible... is there calibration data stored on the device itself?)

Edit: Ubuntu behavior is still about the same!

---

### Post by Ayuthia on 2010-05-05
Thanks for the information.  I think that it is safe to say that the Vista and 2.59 versions are having the left click issue with the default kernel module.  rafiyr has made modifications to the kernel module source so that it will work again.  I am not for sure about when or if it will be updated in the kernel or not.

---

### Post by eNoVa on 2010-05-08
Hey Guys,
I've Good News.
Just playing, out of curiousity, with my 10-wacom.conf,
i got Touch-Click working.

```

Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class identifiers"
	MatchProduct "WACf|FUJ02e5|FUJ02e7"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

 Section "InputClass"
 	Identifier "Wacom N-Trig Pen class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
 	MatchDevicePath "/dev/input/event*"
 	Driver "wacom"
	Option "Button2" "3"
 EndSection

 Section "InputClass" 
 	Identifier "Wacom N-Trig Touch class"
	MatchProduct "HID 1b96:0001|N-Trig Touchscreen"
 	MatchDevicePath "/dev/input/event*"
 	Driver "wacom"
 EndSection
# Created By eNoVa, Inspired by Favux ;P

```

Sometimes the Coursor Jumps to the top-left-corner, no clue why.
Additionally, once you've pressed a bit harder , its getting unusable...


I'm asking myself, is there a possibility to determine how intense a touch was and trigger a specific reaction?
( 
eg. 
light touch : mousemove , 
medium-touch : leftclick ,
 heavy-touch : rightclick
)


eNoVa

---

### Post by Favux on 2010-05-08
Hi eNoVa,

Nice work!

Just add a separate snippet for touch.  Cool.
> I'm asking myself, is there a possibility to determine how intense a touch was and trigger a specific reaction?
That would have to be in the code.  Setting Capacitance never worked right and I noticed they removed it from the xsetwacom commands in the LWP's HOWTO.  And ClickForce and Threshold only apply to the stylus AFAIK.  You can use Assistive Technologies to set a long (duration wise) click to say a right click.  But again it only works for the stylus.

---

### Post by eNoVa on 2010-05-08
> **Favux said:**
> You can use Assistive Technologies.
Could you name me some?

eNoVa

---

### Post by Favux on 2010-05-08
Hi eNoVa,

Sorry, didn't mean to be mysterious.  You go to System > Preferences > Assitive Technologies > Mouse Accessibility > Trigger Secondary Click. You'd have to set the delay right. And again that only works for stylus or a mouse.

---

