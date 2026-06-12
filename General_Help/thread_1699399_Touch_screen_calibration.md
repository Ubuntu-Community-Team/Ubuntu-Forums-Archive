---
title: "Touch screen calibration"
date: 2011-03-03
forum: General Help
---

### Post by zombie on 2011-03-03
Not sure where to ask this so sorry if i've got the wrong section.

I've recently salvaged an old laptop by adding a touch screen overlay in an effort to turn it into a tablet PC. Seems to be working well and once calibrated with xinput_calibrator the touch screen works well enough for my needs.

Trouble is I need to re-calibrate it every time I start an x session. The xinput_calibrator runs and then gives the following message.

--> Making the calibration permanent <--
  copy the snippet below into '/etc/X11/xorg.conf.d/99-calibration.conf'
Section "InputClass"
	Identifier	"calibration"
	MatchProduct	"3M 3M USB Touchscreen - EX II"
	Option	"Calibration"	"2541 14070 13776 2671"
EndSection

Here's where it breaks down for me as I don't have the file referenced on my system.

Should I just create it with the text as above or do I need to put the calibration data somewhere else?

This is a freshly installed 10.10 system with all updates and running the unity interface.

---

### Post by turtle153 on 2011-03-03
I had a problem like this for my graphics tablet, just create the file and it should work. It's a shame x.org doesn't do this automatically, it would save a lot of confusion for beginners.

---

### Post by zombie on 2011-03-03
Thanks mate. Works perfectly :)

---

