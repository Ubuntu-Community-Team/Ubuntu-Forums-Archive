---
title: "Remote Desktop with no Monitor"
date: 2010-02-11
forum: General Help
---

### Post by weaver4 on 2010-02-11
I am using Ubuntu 9.10.  I can do remote desktop into the system with a monitor attached but when I reboot the system without a monitor attached I am unable to do remote desktop into it.  

I want to use this system as a headless system and **only **use remote desktop to control it.

So I guess I need to start X and gnome without a monitor attached.

What do I need to do to get this to run?

---

### Post by jken146 on 2010-02-11
Can you ssh into the box?  You want to do something like [this]("http://stevenharman.net/blog/archive/2008/12/13/vnc-to-a-headless-ubuntu-box.aspx").

---

### Post by slamhound on 2010-02-11
I haven't tried this with 9.10, but I have a similar setup with 9.04. Without a monitor attached, it boots into recovery mode (or something like that) and waits for input from you (to see, boot up without the monitor plugged in, and after a while plug the monitor back in to see what it's doing). I followed a few threads for 9.04 and never saw a good solution, but did find some hacks.  One thing is to trick the computer into thinking that it is plugged into a monitor.  In my case, I had an old dead video card lying around.  Plugged the cable from the headless computer into that video card and now the computer thinks there is a monitor plugged in and it will boot to X for me to log in remotely. There are other hardware hacks like that out there, but this worked for me.

---

### Post by 2hot6ft2 on 2010-02-11
Since you have no monitor to see when to login set it to start without having to login then it should work.
System > Administration > Login Screen
Set it to login automatically.

---

### Post by weaver4 on 2010-02-12
Auto login does not work.  Apperently the intel driver prevents X from starting if there is no monitor present.  I have heard that the vesa driver will start but when I went to modify the /etc/x11/xorg.conf file it is no longer there.  So how do I tell Ubuntu to use vesa driver if there is no longer a xorg.conf file?

---

### Post by weaver4 on 2010-02-12
I found that if I created a /ect/X11/xorg.conf and put this in it then X would start running and I could get to the display by using vnc.  But, when I plugged in a monitor (after the OS has started) their is no display.  Anyone know how to fix that?

```

Section "Device"
        Identifier      "Configured Device"
        Driver  "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync 31-61  
        VertRefresh 50-75
        Modeline "1024x768" 25.20 640 688 784 800 350 410 412 449
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Device"
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

```

---

