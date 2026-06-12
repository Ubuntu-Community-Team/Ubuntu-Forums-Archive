---
title: "Black Desktop With Effects On"
date: 2009-12-26
forum: General Help
---

### Post by Rdogg112 on 2009-12-26
Hello, 

im having a problem with ubuntu  if i turn on effects the desktop goes black and it doesnt show anything, if i turn off it works just fine

Im Using Ati Radeon 9250 (Ancient Graphics Card, I Know)
but in the live CD everything worked ok, i tried downloading driver from the AMD Ati Website but coudnt install , is there an alterntive way/driver i could download?

Thanks In Advance:P

---

### Post by mac9416 on 2009-12-26
Hey, Rdogg112,

There was a driver problem introduced in 9.10 that prevents certain effects from displaying on some older ATI graphics cards. This [solution by zainka]("http://ubuntuforums.org/showpost.php?p=8349820&postcount=46") fixes it: Add the following lines to your /etc/X11/xorg.conf. If the file does not exist, create it.

```
# To avoid unreadable windows.
Section "Device"
	Identifier	"Radeon7500"
	Driver	"ati"
	BusID	"PCI:1:0:0"
	Option	"RenderAccel" "false"
EndSection
```

Good luck!

---

### Post by Rdogg112 on 2009-12-26
> **mac9416 said:**
> Hey, Rdogg112,

There was a driver problem introduced in 9.10 that prevents certain effects from displaying on some older ATI graphics cards. This [solution by zainka]("http://ubuntuforums.org/showpost.php?p=8349820&postcount=46") fixes it: Add the following lines to your /etc/X11/xorg.conf. If the file does not exist, create it.

```
# To avoid unreadable windows.
Section "Device"
    Identifier    "Radeon7500"
    Driver    "ati"
    BusID    "PCI:1:0:0"
    Option    "RenderAccel" "false"
EndSection
```Good luck!

  UnfortunatelyThat Didn't Work :(

---

### Post by mac9416 on 2009-12-26
I should have mentioned it earlier, but did you reboot after adding that? If so, it could be that the two issues are unrelated, and that fix can't help. :(

---

### Post by Rdogg112 on 2009-12-26
yep i rebooted, :(:(

---

