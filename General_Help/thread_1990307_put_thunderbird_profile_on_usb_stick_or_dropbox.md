---
title: "put thunderbird profile on usb stick or dropbox?"
date: 2012-05-29
forum: General Help
---

### Post by qwertyjjj on 2012-05-29
Is there a way to get thunderbird to use the profile on a usb stick or Dropbox?
I hear portable thunderbird only works on Windows and I don't want to use wine as it's mostly always out of date so nothing works forever.

---

### Post by oldfred on 2012-05-30
If you do not have path mounted when you open Thunderbird, you will have problems.

But I have my Thunderbird profile in a NTFS partition that I used to share with XP. I have used the same profile since 6.06 (I think). I did move it from a FAT partition to NTFS with 9.10 and regularly copy the entire profile to my laptop when I travel and then back when I get home.

You really just have to edit profile.ini with the path and tell it that it is not the local copy.
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

