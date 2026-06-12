---
title: "Rhythmbox and m4a"
date: 2006-03-01
forum: General Help
---

### Post by Sherlock Holmboy on 2006-03-01
when i try to open an m4a with rythmbox it gives me the error "file is not an audio stream". i have already installed the gstreamer-plugins metapackage and still doesn't work.  what do i need to do to install to make this work?:-k

---

### Post by skymt on 2006-03-01
You need to enable Multiverse and install gstreamer0.8-plugins-multiverse. That includes gstreamer0.8-faac, a plugin for m4a files (which are really AAC). For details, see [RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats") and [AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto").

---

### Post by mcgregorandrew on 2008-01-11
Thanks for that.  Just a note that instructions vary from release to release, but the links showed it all.  For the record, on Ubuntu 6.06 I needed to do:


Ubuntu 6.06 LTS (Dapper Drake)

      Install the gstreamer0.10-plugins-bad-multiverse package. (Note: some people may need to also install gstreamer0.10-plugins-bad to make it work.)

---

### Post by hanspb on 2008-01-17
Hi, I have both gstreamer0.10-plugins-bad-multiverse and gstreamer0.10-plugins-bad installed, but still Rhythmbox won't play my m4a files properly. Totem does it perfectly, but I happen to prefer rhythmbox for music playing. Any Ideas?

---

### Post by lostthewar on 2008-01-22
> **hanspb said:**
> Hi, I have both gstreamer0.10-plugins-bad-multiverse and gstreamer0.10-plugins-bad installed, but still Rhythmbox won't play my m4a files properly. Totem does it perfectly, but I happen to prefer rhythmbox for music playing. Any Ideas?

follow skymt's instructions; it worked for me.

---

### Post by hanspb on 2008-01-23
Hm. Gstreamer 0.8 isn't even in the Gutsy repos... And yes, I have Multiverse enabled. Also, I don't understand why something supported in 0.8 is not in 0.10?

---

### Post by groupmsl on 2008-02-04
> **hanspb said:**
> Hm. Gstreamer 0.8 isn't even in the Gutsy repos... And yes, I have Multiverse enabled. Also, I don't understand why something supported in 0.8 is not in 0.10?

I have the same problem, I have got the gstreamer1.0 packages installed, and totem will play m4a files, but rhythmbox wont?!! If anyone can help that would be great!

---

