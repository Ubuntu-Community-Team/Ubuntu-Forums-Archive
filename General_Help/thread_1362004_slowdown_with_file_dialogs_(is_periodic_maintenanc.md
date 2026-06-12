---
title: "slowdown with file dialogs (is periodic maintenance needed?)"
date: 2009-12-22
forum: General Help
---

### Post by mas2265 on 2009-12-22
Hello,

I have recently noticed on my computer that it has slowed down in various places where it used to not.  I think I'll first try to focus on one aspect: Oftentimes when I open save-as or open dialogs in applications, or if I browse files in Gnome's browser, it takes a long time to load the contents of the current directory, not redrawing or responding to user input in the meantime.  These are directories on the laptop's primary, internal hard drive.

I am guessing that there are a whole variety of possible causes for this, but where do I start looking?  Is there any periodic maintenance (eg: defragmentation?) that ought to be done on an Ubuntu machine that I might have failed to do? (My hard drive is now 2/3 full, but there should be plenty of space remaining.)

Could it be that something processor-intensive is running that I'm not aware of?  Would [ps -e --sort=-%cpu] provide this information?

I'm currently using Ubuntu 9.04 (though maybe I should upgrade?).

Thanks in advance.  Any pointers would be appreciated.

Michal

---

### Post by dcstar on 2009-12-22
> **mas2265 said:**
> Hello,

I have recently noticed on my computer that it has slowed down in various places where it used to not.  I think I'll first try to focus on one aspect: Oftentimes when I open save-as or open dialogs in applications, or if I browse files in Gnome's browser, it takes a long time to load the contents of the current directory, not redrawing or responding to user input in the meantime.  These are directories on the laptop's primary, internal hard drive.

I am guessing that there are a whole variety of possible causes for this, but where do I start looking?  Is there any periodic maintenance (eg: defragmentation?) that ought to be done on an Ubuntu machine that I might have failed to do? (My hard drive is now 2/3 full, but there should be plenty of space remaining.)

Could it be that something processor-intensive is running that I'm not aware of?  Would [ps -e --sort=-%cpu] provide this information?

I'm currently using Ubuntu 9.04 (though maybe I should upgrade?).

Thanks in advance.  Any pointers would be appreciated.


Does your system work slower or faster if you boot it up without a network connection?

Also, make sure SMART is enabled in your BIOS because if your have a bad sector on your hard drive then that can make a system appear slow as it retries.

---

### Post by mas2265 on 2009-12-23
Thanks for the advice.  I tried disabling what I thought was a network interface, in the bios settings, but this didn't seem to disable the wi-fi; I'll look again tomorrow.  I didn't see a SMART setting in the bios settings.  I have a Dell Inspiron from summer 2007.

Shortly after booting, things seemed fine, but then a little while into usage (with Firefox (with a handful of tabs), Thunderbird, Pidgin, and Gedit), there was a decrease in responsiveness and I could hear the hard drive most of the time.

Michal

---

