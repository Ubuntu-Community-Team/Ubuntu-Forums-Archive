---
title: "gtkperf (only Text-Tests!) very slow."
date: 2010-06-06
forum: General Help
---

### Post by leonidas666 on 2010-06-06
My Ubuntu (10.04) feels a bit slow, so i tried gtkperf to test it. After running gtkperf -a -c 1000 i got the following:

```
lorenz@leonidas:~$ gtkperf -a -c 1000

(gtkperf:2329): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkperf:2329): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
GtkPerf 0.40 - Starting testing: Sun Jun  6 22:37:39 2010

GtkEntry - time:  0,84
GtkComboBox - time: 21,67
GtkComboBoxEntry - time: 13,97
GtkSpinButton - time:  3,40
GtkProgressBar - time:  5,46
GtkToggleButton - time:  3,99
GtkCheckButton - time:  3,32
GtkRadioButton - time:  5,16
GtkTextView - Add text - time: 149,23
GtkTextView - Scroll - time: 11,07
GtkDrawingArea - Lines - time: 13,27
GtkDrawingArea - Circles - time: 20,08
GtkDrawingArea - Text - time: 107,64
GtkDrawingArea - Pixbufs - time:  5,15
 --- 
Total time: 364,29

Quitting..

```

I have seen the result of other people this test, and of course some are overall faster (actually most, definitely my computer is  rather old and slow), and some are overall slower. 
But what i find very wrong here are the tests "GtkTextView - Add text" and "GtkDrawingArea - Text". These tests seem to take a disproportionally amount of time, even considering that the other tests also don't finish too fast (compared to the gtkperf data i have seen from other people). So think there is something wrong in this regard with my setup.

What could it be? 
A Font-Problem? Do i have any strange Fonts installed? I did a fresh install of ubuntu 10.04 (no update), and created a fresh user with a empty home directory -> same result.
A video card driver problem? I have a NVIDIA card, and i am using the binary nvidia driver which was suggested by ubuntu. I have tried Version 173 (the latest binary driver for my card, according to nvidia) and Version 96, and also the nouveau driver -> same result.

Any other idea what could be wrong here? Or is this normal behavior?

---

