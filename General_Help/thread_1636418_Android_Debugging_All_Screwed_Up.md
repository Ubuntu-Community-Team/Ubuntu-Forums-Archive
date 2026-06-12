---
title: "Android Debugging All Screwed Up"
date: 2010-12-03
forum: General Help
---

### Post by idi0tf0wl on 2010-12-03
Howdy-ho all!

This hasn't happened to me before, but I develop for the Android platform and (perhaps needless to say) I really need to be able to debug on a real device. On past installs, my device was recognized automatically and debugging was as easy as checking "debug" in the Android's settings, but now (after updating to Maverick from Lucid) the phone registers with adb as ??????????

Anyway, I Googled around for a bit and came upon this page: [http://developer.android.com/guide/developing/device.html](http://developer.android.com/guide/developing/device.html)

It mentions some necessary tasks for set-up on Ubuntu, but only mentions this process for Dapper/Gutsy/Hardy. Is there any personal experience out there that can confirm that this works and/or is necessary on Maverick? Any other suggestions?

Thanks and much love!<3

---

### Post by idi0tf0wl on 2010-12-03
Alright folks, this was a somewhat urgent topic for me, so I pioneered on ahead and just created the /etc/udev/rules.d/51-android.rules and edited it according to the rules for Hardy at

[http://developer.android.com/guide/developing/device.html](http://developer.android.com/guide/developing/device.html)

Everything works famously now. None of this was necessary in Lucid, but for those of you running Maverick and programming for the Android platform (apparently, that combination isn't as widespread as I thought it would be), you can go to that url and get yourself fixed up.

Cheers!

---

