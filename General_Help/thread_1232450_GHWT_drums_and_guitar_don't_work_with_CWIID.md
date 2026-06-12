---
title: "GHWT drums and guitar don't work with CWIID"
date: 2009-08-05
forum: General Help
---

### Post by ShamanSTK on 2009-08-05
After doing some research, I found this [http://abstrakraft.org/cwiid/discussion/message/24431#24431](http://abstrakraft.org/cwiid/discussion/message/24431#24431)

it appears its a cwiid issue and theres a patch, but I can not for the life of me figure out how to either apply the patch or compile the source (apparently it needs an older version of gcc or something like that). is there an easy fix that eludes me?

bonus question: when is the bluez and wiimote issue going to be resolved?

---

### Post by ShamanSTK on 2009-08-05
i did it! apply the patches above, i did it manually because i couldn't figure out how to patch it. after i recompiled it. it worked fine. GHTW drums appear as a classic controller

---

### Post by marshmallow1304 on 2009-08-06
Any chance of uploading the edited source as it was right before you compiled it?  I'd like to compile it for 64-bit.

Thanks.

---

### Post by ShamanSTK on 2009-08-06
its an archive of my source folder after i ran ./configure and make. i delete the debs made by checkinstall so it should be all ready to go. let me know how it goes

---

### Post by marshmallow1304 on 2009-08-06
> **ShamanSTK said:**
> its an archive of my source folder after i ran ./configure and make.

That's already been compiled, so it won't work for me.  I can follow the link in the original post and figure it out.  Thanks anyway.  :D

---

### Post by ShamanSTK on 2009-08-07
yea, sorry about that, I didn't think to compile in a different directory while I was trying it out. You can just replace the header files with the ones i posted if you're too lazy to patch it manually

---

### Post by escu on 2009-11-23
Thanks ShamanSTK for the .deb, but my guitar isn't responding in wmgui. I've uninstalled previus packcage and installed your deb and the nunchuck is responding but not the GHWT guitar (i haven't classic controller to test) 
I'll try to compile myself and test that zip

---

### Post by sidrit on 2010-02-10
ooooooookay.
finally got it sorted.

downloaded the source of cwiid 0.6.
patched the hci_red function.
patched and removed the decode function and add the headers for the ghwt and compiled. now it works.

here's a write-up about it 
[http://sidrit.wordpress.com/2010/02/10/frets-on-fire-with-guitar-hero-world-tour-ghwt-on-ubuntu/]("http://sidrit.wordpress.com/2010/02/10/frets-on-fire-with-guitar-hero-world-tour-ghwt-on-ubuntu/")

---

