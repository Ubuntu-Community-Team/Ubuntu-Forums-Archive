---
title: "KVM switch is not allowing monitor detection"
date: 2009-10-30
forum: General Help
---

### Post by SctClsn on 2009-10-30
I am running a fresh Ubuntu 9.1 on an eMachines desktop with an on board intel 82856G video chip.  After much searching, I was just about to blame the intel video driver for my only having 800x600 and 640x480 as monitor resolution choices when the light went on.  I have this machine, a PIII running Debian server (no GUI) and a Mac G4 all running through a 4 port usb KVM switch (generic).  The Mac gives me full 1024x768 resolution.  If I plug direct, so does the Ubuntu machine.  Something is keeping the Dell 19" LCD monitor from being detected through the KVM (it is identified perfectly when connected direct).

xorg.conf is as follows weather direct connect or through the KVM:

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


xorg.conf also has this line:

# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.

My question is; 
Is there anywhere I can hard set what is detected when i'm directly connected so that it isn't overridden by autodetect when i reboot using the KVM? and where would I find the settings used when i'm directly connected, if not in xorg.conf?

My knees and back really don't want to go back to crawling under the desk all the time and my wallet would rather not spring for more monitors.

Thanks for all the help I've already pulled from this forum and for any help w/ this.

---

### Post by SctClsn on 2009-11-01
Continued searching turned up [this site]("http://robert.penz.name/219/workaround-for-the-ubuntu-problem-with-kvm-switches/") with a workaround for this problem.  Apparently editing the xorg.conf file does still keep forced resolution settings.

I'm now running at 1024x768.

And my knees are still happy.

Thanks to Robert Penz for the helpful blog site.

---

