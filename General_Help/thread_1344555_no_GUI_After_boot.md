---
title: "no GUI After boot"
date: 2009-12-03
forum: General Help
---

### Post by The Converted on 2009-12-03
Hi guys. I've been lurking for a while now and decided to register since i couldn't find a solution to my problem. I've installed ubuntu studio 9.10 a while back but have since been unable to boot all the way to the desktop. what i have is a blank screen with the cursor. nothing else. thinking that this was the loggin screen i entered my details and the only change is the cursor changing from pointer to loading. the machine spec is P4 3GHz 2 GB ddr800 ati radeon hd 3650 agp. I'm thinking this is driver/gpu issue but since i'm a newbie i'm having trouble sorting this one out. i've tried repairing broken packages and updating the grub loader. no joy. unless of course everybody has lied to me and i'm a complete idiot and should never touch a pc again.

---

### Post by u.b.u.n.t.u on 2009-12-03
> **The Converted said:**
> Hi guys. I've been lurking for a while now and decided to register since i couldn't find a solution to my problem. I've installed ubuntu studio 9.10 a while back but have since been unable to boot all the way to the desktop. what i have is a blank screen with the cursor. nothing else. thinking that this was the loggin screen i entered my details and the only change is the cursor changing from pointer to loading. the machine spec is P4 3GHz 2 GB ddr800 ati radeon hd 3650 agp. I'm thinking this is driver/gpu issue but since i'm a newbie i'm having trouble sorting this one out. i've tried repairing broken packages and updating the grub loader. no joy. unless of course everybody has lied to me and i'm a complete idiot and should never touch a pc again.

Hi and welcome to Ubuntu community.

You say you installed Ubuntu 9.10. So does that mean it was a successful install and was working for a time?

When a computer is working, and then stops working, one of the first questions is, what was installed or changed and this is what I ask.

Did you change the graphics settings at all?

---

### Post by The Converted on 2009-12-03
To answer you first question. yes it was a fresh install and so far as working i could get into the prompt, access the internet, update the system, etc. the only real issue was getting the gui to function *correctly.* Since posting i have (as luck would have it) been successful in getting the gui up and running. however this is without driver support (using fglrx). initially i was trying to install with this:

sudo apt-get install xorg-driver-fglrx linux-restricted-modules

and got a response saying that the module/driver cannot be found

so my brain farted and i removed the *linux-restricted-modules* section rebooted and presto! The gui was working. I do however suspect that this is more of a patch job rather than a fix.

---

### Post by The Converted on 2009-12-03
Okay so after kicking myself for being an idiot i installed the hardware drivers for my card the went to check xorg.conf since before this it was empty and got this:

 Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "fglrx"
EndSection

which i then edited as per the advice i received elsewhere (can't remember the site)
with the following:

Section "Extensions"
            Option       "Composite" "disable"
EndSection

Which messed up the system again (driver didn't load correctly)
so i removed this line and everything is now working. if you see anything i missed let me know. 
and my apologies for being an ID10T.

---

### Post by u.b.u.n.t.u on 2009-12-03
> **The Converted said:**
> now working.

Congratulations!

You are reporting it working so there really isn't anything to add.

Maybe backup the xorg.conf file to an external source.

---

### Post by QIII on 2009-12-03
Congrats on your success.

You are only an India Delta One Zero Tango if you do not learn from your experience.

Nobody comes into the world knowing everything.  Well, maybe except for me...

---

