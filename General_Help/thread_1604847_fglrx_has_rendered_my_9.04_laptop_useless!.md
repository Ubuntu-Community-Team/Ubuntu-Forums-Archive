---
title: "fglrx has rendered my 9.04 laptop useless!"
date: 2010-10-24
forum: General Help
---

### Post by Darkness Falls on 2010-10-24
I have a feeling I've done something rather rash.

I've been playing around with video drivers in an attempt to get better 3D-acceleration support out of my Radeon ATI video card on my HP dv7 laptop. (For information, I'm currently running 9.04 Jaunty Jackalope.) After doing some research online, I came to understand that a package called xorg-drivers-fglrx (and its associated dependencies) sometimes provides better graphics, so I downloaded and installed it; the web page I was on recommended I edit my xorg.conf file to point to the new driver, which I did, after making a backup of it just in case.

The problem is, of course, that when I rebooted, fglrx didn't work at all, and the laptop hangs on boot-up. I got into it again via my installation disk and managed to re-edit the xorg.conf file back to what it was before, thinking that would fix the problem; but apparently fglrx is still messing it up, because it still hangs at boot-up.

I then tried to get in via the installation disk and run a
```
sudo apt-get remove --purge xorg-drivers-fglrx
```
but it returned that no such package was installed, so none has been removed.

This is worrying me now, and I'm starting to wish I'd just settled for what I had. Is there any way to just get Ubuntu to use its default video driver again, so I can get rid of this thing? Failing that, is there any way to 'fix' fglrx to make it do its job properly?

Thanks in advance,

D.F.

---

