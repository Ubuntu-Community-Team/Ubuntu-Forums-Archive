---
title: "Dual Monitor Support with NVidia"
date: 2010-05-08
forum: General Help
---

### Post by timhaughton on 2010-05-08
I've managed to get dual monitor support working, but it seems a little sub-standard.

 - I can't find how to alter the relative y offsets of each screen
 - I can't drag windows from one side to the other

Any solutions?

Cheers

---

### Post by spoon_ on 2010-05-08
If you installed the driver from nvidia's website, you should be able to go to System > Preferences > Nvidia X Server Settings and from there set it to TwinView mode so that you can drag windows from one screen to the other.

If you installed the driver from the repository, I think you also need to install the nvidia-settings package and then do as above.

---

### Post by timhaughton on 2010-05-08
Thanks for that. I had selected Twin view but it had somehow got unselected. The y offset seems limited to offsetting the smaller monitor within the y dimension of the larger monitor which isn't ideal, but not a killer.

Thanks again.

---

### Post by spoon_ on 2010-05-08
Oh you may have to run nvidia-settings as root, set it to the settings you like, and then click the "save to xorg.conf" button so that it remembers your settings. I think I had the forgetting problem too before I did that.

---

