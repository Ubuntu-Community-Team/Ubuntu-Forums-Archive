---
title: "Display size problem nvidia 8400gs 1600x1024 display"
date: 2010-02-10
forum: General Help
---

### Post by gtr@frii.com on 2010-02-10
This is with 9.10 2.6.31-19.  At some point, I believe with the upgrade to 31-19, my display got messed up.  The power icon (correct name??? when you click on it brings up the logout, suspend, reboot, etc. dialogue) moved from the right top edge to approximately 2/3 across right top.  That is still usable, however, I am running nxserver on this machine and a windows vm in virtualbox.  After the power icon moved, I can no longer access applications | places | system from an nxclient (they are no longer visible) and 2 of the 5 quick launch icons are also missing in an nxclient.  Likewise the display in virtualbox with vbox-guest-add-ons enabled no longer resizes.
To summarize the above, things look okay on the ubuntu 9.10 desktop except for the power icon (the trash icon on the bottom is also about 2/3 of the way over instead of on the right edge).  However, running nxclient from another machine does not work in either minimized or maximized mode - I can't access applications | places | system because they are not present in the display.  This all worked just fine a week or so ago.  My guess is that I have a mismatch in display size.  my xorg.conf file has the following in the monitor section

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 2005FPW"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Additionally, I can successfully save from gksudo nvidia-settings.

Any ideas?

---

