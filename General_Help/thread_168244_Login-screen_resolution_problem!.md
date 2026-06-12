---
title: "Login-screen resolution problem!"
date: 2006-04-30
forum: General Help
---

### Post by Morgon123 on 2006-04-30
Here's the problem: while installing, the highest resolution I chose was 1024x768, because that's what I used with Windows. Now I wanted to change the resolution to 1280x1024, so I added this to my xorg.conf file. Now, my login screen gets all "flickery" because I suppose he uses a resolution that's too high. On the desktop, 1280x1024 works fine, but in the menu, I can now also choose 1600x1200 and so I suppose that's the resolution he uses for the login-screen. Is there any way to change this? Removing the 1280x1024 from xorg.cong didn't help...

---

### Post by hollywoodb on 2006-04-30
```

Section "Screen"

----------------ignore next 3 lines-----------------
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV31 [GeForce FX 5600]"
        Monitor         "Generic Monitor"
--------------------------------------------------

        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

The Screen section of xorg.conf should look something like that.

---

### Post by Morgon123 on 2006-04-30
Thank you, problem solved!

---

