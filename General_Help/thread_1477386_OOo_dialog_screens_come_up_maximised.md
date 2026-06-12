---
title: "OOo dialog screens come up maximised"
date: 2010-05-08
forum: General Help
---

### Post by TMD on 2010-05-08
Hello! I looked on the forums and bug tracker and couldn't this, but apols if it's already been mentioned. When I use a little helper window (like the find and replace dialog) in OOo 3.2 on 10.04 UNR it always comes up maximized, which is kind of irritating, because I have to restore it before it's usable. It's weird that such a window should even have a maximize button, but there you go. No biggie, clearly, but if anyone knew of a workaround that would be great! I'm using the clearlooks theme, although I tried with the new black shiny one and it seems to exhibit the same problem. 

Other than that, lovin' 10.04

Thanks, t

---

### Post by CoreyB. on 2010-05-08
UNE uses a program called maximus, it is designed to maximize windows because the netbook screen is small.  This is an unfortunate side effect.  I don't know of any work around, but then I've never really tried to work around this.  One way might be to uninstall maximus, but then none of your windows will maximize automatically.

---

### Post by TMD on 2010-05-09
Thanks! I should have said, this wasn't a problem with Karmic & 3.1.

Hmm. It seems to me it's just doing what it's supposed to do, and the openoffice folks broke it somehow, maybe by changing the frame type of the dialogs. I guess I'll head to the OOo support.

---

### Post by frambla on 2010-06-17
I had the same issue and I agree it was really irritating ;-)
Well, maybe it could help you. I've used the "xprop" command to identify Window Class for OpenOffice.org dialogs and then added an exception in Maximus settings for this Window Class.

Running "xprop" and selecting one of the OpenOffice.org afected dialogs returned: ```
WM_CLASS(STRING) = "VCLSalFrame", "OpenOffice.org 3.2"
``` 

Given I want main OpenOffice.org windows maximized, I used the "VLCSalFrame" string. To change Maximus configuration, open gconf-editor and search the apps/maximus/exclude_class key. Add "VCLSalFrame" to this key and... ooala! No more OpenOffice.org maximized dialogs!

---

### Post by TMD on 2010-06-18
Ah, very nice. My OOo writer comes up unmaximized now, but that is a small price to pay, frankly. And thanks for taking me through the steps you took, it's really appreciated! Cheers, dude, you rock!

---

### Post by Goatrancer on 2010-11-10
Yeah I have this problem too. I like Maximus for most things, and I would like to keep OO in full screen. If the problem gets annoying enough, I might try Frambla's suggestion, but I would really prefer if Maximus would only maximize actual windows, but not dialog boxes.

---

