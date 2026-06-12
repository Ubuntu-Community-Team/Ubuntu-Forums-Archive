---
title: "Power button to shutdown immediately"
date: 2010-04-02
forum: General Help
---

### Post by chewearn on 2010-04-02
Running Karmic Koala.

Recently, for unknown reason, the USB keyboard and mouse refused to work at all.  Re-plugging the USB does not help.  Meanwhile, the screen stayed blank (because it's locked).

So, I figured, press the power button (that's the the hardware switch on the desktop case).  I expect the PC to shutdown immediately.  Instead, the unlock screen dialog pops up.  Since the keyboard and mouse is not responding, there is nothing I could do further.

In the end, I have to hard reset.

Now, the question is, how can I change the power button behaviour to what I expected?  I.e. when the power button is pressed, it means shutdown immediately, no ifs or buts.  Thanks! :)

---

### Post by Primefalcon on 2010-04-02
Go to power options in your system menu, option should be in there

---

### Post by jrdm on 2010-04-02
System>preferences>Power Manegement>General

Switch the option "when the power button is pressed" to switch off.

---

### Post by chewearn on 2010-04-02
Thanks for the replies.  While the option is there in the Power Management dialog, it does not work when the PC is locked.

---

### Post by mimor on 2010-04-02
Some systems provide 'power button' action in the BIOS.
You can also hold the powerbutton pressed till the pc switches off.
(takes about 7sec's)

---

### Post by chewearn on 2010-04-02
> **mimor said:**
> Some systems provide 'power button' action in the BIOS.
You can also hold the powerbutton pressed till the pc switches off.
(takes about 7sec's)

Thanks for the suggestion.

Yes, press and hold for more than 4 seconds will switch off.  This is same as pressing the hard reset, i.e. the OS will not be given the chance to shutdown gracefully.

I am looking for functional equivalent of pressing Power button executing "sudo poweroff", where the OS can terminate properly.

---

