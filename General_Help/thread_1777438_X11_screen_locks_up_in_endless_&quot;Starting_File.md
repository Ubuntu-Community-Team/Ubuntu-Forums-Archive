---
title: "X11 screen locks up in endless &quot;Starting File Manager&quot; loop."
date: 2011-06-07
forum: General Help
---

### Post by DRNewcomb on 2011-06-07
I have a generic PC (VIA chipset, AMD 1.8 GHz, old NVIDIA card, etc) running Ubuntu 10.04 side-by-side with a Windows XP box. The Ubuntu box can see and mount some of the Windows disks via SAMBA. Recently, I had a little hardware problems with the Ubuntu box but cleaned the fans and reseated cards and things seemed better. 

Today the Ubuntu box rebooted and when it came back up I could log in OK but then the X11 GUI locked up in a continuous "Starting File Manager" loop. If I click anything the taskbars go away showing only a blank wallpaper screen then the taskbars return but but will recycle if I click on anything. I can reboot in recovery mode and have applied all updates from that screen. The underlying Linux seems to be fine. I can CTRL+ALT+F1 and get a terminal screen that works fine.   

I have searched the forums for solutions for this problem and the answers seem to be all over the map. Some suggested solutions were to reload Ubuntu. It would be a shame to have to resort to this because Linux seems fine. The only problem seems to be with the windowing system. Are there any tricks for resetting the File Manager or whatever might be hanging up? 

Update: On a suggestion from the local LUG I added a 2nd user account and tested that account. It experiences exactly the same problem as the other account. So, the problem is not account-specific.

Thanks

---

### Post by DRNewcomb on 2011-06-08
Update: After seeing that the .xsession-errors file suggested that something might be wrong with either  udisks or dbus, I did a "aptitude reload" of both those packages. No change of status :-(

---

