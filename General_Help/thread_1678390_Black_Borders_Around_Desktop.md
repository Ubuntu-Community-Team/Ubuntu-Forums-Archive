---
title: "Black Borders Around Desktop"
date: 2011-01-30
forum: General Help
---

### Post by chazdg24 on 2011-01-30
Hey everyone, I'm new here, so I apologize for sounding dumb.

I have an issue with my ATI 5800 card.  Installation was flawless (dual boot with Windows 7 64 bit with all updates installed.  Upon reboot, I have a black border around the entire Desktop.  My screen resolution is set to maximum.

Being new to all this, I am somewhat perplexed how the ATI Catalyst Control Center works.  In Windows 7, this is the Scaling Option in the Catalyst Control Center which can easily rectify the situation.  I have verified that the Catalyst Control Center is installed but I have no idea how to proceed to fix this.

I have been searching Google for two days with no luck - lots of suggestions, but no fix.  Can someone point me in the right direction as I would like to learn and understand how to use this OS.  Thanks in advance everyone.

---

### Post by Frogs Hair on 2011-01-30
Hi and Welcome

This may be way too simple but check just in case. Go to System > Preferences > Appearance Preferences > Background Tab and check the style setting . Some backgrounds will have the edges cut off depending on the setting , it  looks like a black picture frame.

Next I would be checking scaling and or resolution settings . If the entire screen is included it is not a background setting.

---

### Post by chazdg24 on 2011-01-30
> **Frogs Hair said:**
> Hi and Welcome

This may be way too simple but check just in case. Go to System > Preferences > Appearance Preferences > Background Tab and check the style setting . Some backgrounds will have the edges cut off depending on the setting , it  looks like a black picture frame.

Next I would be checking scaling and or resolution settings . If the entire screen is included it is not a background setting.

Not to sound completely idiotic, where is the scaling option?  I just cant seem to find it.  Sorry for all of these simple questions.

---

### Post by chazdg24 on 2011-01-31
Well, the black border issue has been resolved.  Screen resolution when changed, would stay the the same. I then noticed the the ATI Catalyst Control Center was not to be found even though the package was installed.  So I uninstalled it along with the drivers and reinstalled.  Now I was able to change the screen resolution and have access to the ATI Catalyst Control Center.

The only thing I have not figured out is the scaling option and where it might be.

---

### Post by chazdg24 on 2011-03-02
The ATI CCC does not work properly after I installed the updates for Ubuntu 10.10 yesterday.  The issue with scaling is back which requires that I fix it (black borders around desktop) every time I boot into Ubuntu.  After I adjust it in CCC, the same problem occurs as soon as I log in after logging out.  Does anyone else have this problem? The screen resolution is 1920 x 1080.  The only resolution that works without a black border is 1280 x 720.

More importantly, is there a fix for this issue?

---

### Post by chazdg24 on 2011-03-03
Anybody...

There must be a fix for this issue.

---

### Post by Veld on 2011-03-05
If I understand correctly, you have a black frame around the picture, right? I have the very same issue both in Windows XP and Xubuntu 10.10. Everything is fine if I uninstall the proprietary drivers for my integrated ATI graphics card, though.

---

### Post by chazdg24 on 2011-03-05
Well, I fixed this issue for now.  I reinstalled the driver and rebooted.  Still have black borders.  I then changed the screen resolution downward until the black borders were gone.  I then logged out.  When I logged back in, I noticed that the black borders did not return.  I then went back up to 1920 x 1080 and logged out.  I logged back in and the problem was solved on all screen resolutions.  

This is definitely a driver issue.  I was about to do what you did, install the ATI driver until I stumbled upon this quirky fix.

---

