---
title: "Community advice regarding slow digikam bug?"
date: 2010-10-17
forum: General Help
---

### Post by mindsound on 2010-10-17
Heyo!  Sorry this is complicated.

I just upgraded to Ubuntu 10.10 and it's been ... rocky.  I do photography with a Nikon D90.  In 9.10 and 10.4, the D90 worked flawlessly via [_USB PTP_]("http://en.wikipedia.org/wiki/Picture_Transfer_Protocol") with little or no effort on my part.  I have been using digiKam for years and I would like to keep using it.  Unfortunately, at some point in the 10.4 updates I [_got burned by this exiv2 bug_]("https://bugs.launchpad.net/ubuntu/+source/exiv2/+bug/596327"); importing a couple hundred pictures takes me hours.  That's not cool.

After upgrading to 10.10, to my surprise, the D90 didn't even work with gphoto2 anymore.  Oh well.  I upgraded to libgphoto2 2.4.10.1 from source, which was easy.  That put me back in business, but the exiv2 bug is still in full effect.  I tried compiling exiv2 and libkexiv2 from scratch ([_per this digikam-users thread_]("http://osdir.com/ml/digikam-users/2010-06/msg00046.html")) but I can't figure out how to build digikam.  It uses cmake and I'm totally unfamiliar with that and with building KDE apps in general.

I have been poking around all day.  I see that shotwell has now replaced f-spot.  I looked at shotwell but it seems to lack critical features (to me) that so far only digikam provides (rich EXIF and metadata display, folder-based organization).

I guess I'm wondering ... where do I go from here?  I'm not familiar with Ubuntu's triage and update process.  Allegedly, exiv2 0.20 fixes the slowdown.  Is there any chance exiv2 0.20 will get pushed out in 10.10?  Does anyone have a concise recipe for building digikam?  Should I reboot and buy Lightroom?  :) I have 20,000 pictures in my digikam setup so this is serious business for me.

Let me know if there's any further pertinent detail I can provide.  I'm open to any advice.

---

### Post by Josh McFadden on 2010-10-20
Well, never mind...

I raged out and figured out how to patch exiv2 / rebuild kdegraphics.  I'm not happy with all these source debs but whatever.  Submitted the patch to [https://bugs.launchpad.net/ubuntu/+source/exiv2/+bug/596327](https://bugs.launchpad.net/ubuntu/+source/exiv2/+bug/596327)

---

