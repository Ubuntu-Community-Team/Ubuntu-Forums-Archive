---
title: "ubuntu won't fully boot after Plymouth change"
date: 2010-08-23
forum: General Help
---

### Post by AaronStarr on 2010-08-23
I changed the Plymouth Theme following the direction on this page:

[http://n00bsonubuntu.com/content/install-extra-plymouth-themes-ubuntu-1004-lts-lucid-lynx](http://n00bsonubuntu.com/content/install-extra-plymouth-themes-ubuntu-1004-lts-lucid-lynx)

Basically, I put this in the Terminal:
**sudo update-alternatives --config default.plymouth**

I then selected a theme (I believe it was spinning something or other). Then I entered:
**sudo update-initramfs -u**

Now, when I boot up, it just sits on a blank screen after I select to start up with ubuntu.

Any thoughts? I have no idea what to do. I'm still an ubuntu n00bie. I can't boot into ubuntu at all.

---

### Post by AaronStarr on 2010-08-28
Does anybody have any ideas or know where to point me to, to solve this?

---

### Post by bcatt on 2010-09-29
Same problem here...anyone?

---

### Post by bovinius on 2010-10-05
during the boot do you get a completely black screen ( ie not backlit)?
try <ctrl><option/alt><f3> right after getting the completely black screen. 
then you should become backlit. 
If this happens then hit <ctrl><option/alt><f7>
you can then log in as normal.

give it a try or 2 or 3

---

