---
title: "Touchpad refuses to die."
date: 2006-02-26
forum: General Help
---

### Post by HippoMan on 2006-02-26
Has anyone figured out how to get the synaptics touchpad to totally, completely, and irrevocably be turned off while running kubuntu under Breezy on my Dell Inspiron 9300? I don't want tapping, I don't want sliding, and I don't want ANYTHING to work on the touchpad. I want it to behave like a dead piece of metal with no more functionality than the rest of the material that makes up the case of my machine.

Everything I have tried has no effect, and I can't kill the touchpad functionality. It keeps on responding to touches, slides, and taps, no matter what I do. It's like I'm in the movie *Night Of The Living Dead Touchpad*.

Here are all the things that I have done and am doing:

1. I have the following items installed via apt:

    ksynaptics
    xorg-driver-synaptics

2. I have the following lines in xorg.conf:
```
  Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"      "true"
        Option          "Device"              "/dev/psaux"
        Option          "Protocol"            "auto-dev"
        Option          "HorizScrollDelta"    "0"
        Option          "SHMConfig"           "on"
  EndSection
``` 
3. I run the following command:

   synclient TouchpadOff=1

4. I went into **KDE Control Center->Peripherals->Touch Pad** and I set the following items:

... in the **General** section: **Touch Pad** is **off**, **Disable touchpad when typing** is not set, and **ALPS touch-pad** is not set.

... in the **Tapping** section: **Enable tapping** is not set, and **Enable faster-tapping** is not set.

... in the **Scrolling** section: **Enable horizontal scrolling** is not set, **Enable vertical scrolling** is not set, **Enable circular scrolling** is not set, **continue scrolling** is not set, and **cursor movement** is not set.

But still, even after rebooting, my touchpad is still active. Earlier, I was running debian/testing on that same machine, and doing numbers 1, 2, and 4 did indeed successfully kill my touchpad.

What do I have to do under kubuntu/breezy to kill it in the same way?

Thanks in advance.

---

### Post by HippoMan on 2006-02-27
I finally found the answer:[ http://www.linuxquestions.org/questions/showthread.php?p=1985763#post1985763]("http://www.linuxquestions.org/questions/showthread.php?p=1985763#post1985763")

What puzzles me is why all the other stuff I tried didn't work, especially since that scenario *does* work to disable the touchpad under debian/testing.

Oh well ... I guess I'll leave that question to the philosophers.  The important thing is that now, my touchpad has finally become the useless piece of cold, dead metal that I've been yearning for.

---

