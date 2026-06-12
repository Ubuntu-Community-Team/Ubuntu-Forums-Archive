---
title: "nrg2iso - is it broken???"
date: 2010-08-26
forum: General Help
---

### Post by omelette on 2010-08-26
I have used nrg2iso in the past without problems - it worked great!  However, now when I generate nrg files with Nero and convert them with nrg2iso, while the resulting ISO image mounts, the built-in mounter shows nothing when opened, while gmountiso complains that an error has occurred when it tries mounting the image.

EDIT: - The above was to be my question.  I then decided to try and get to the bottom of the matter myself and this is what I found...

When I use Nero to create an NRG image file using the contents of a mounted CUE/BIN image (using CDEMU), nrg2iso creates a 100% working ISO from the resultant NRG image.  Whereas if I create the NRG image with Nero directly from the CUE/BIN image, nrg2iso creates an ISO that is 'corrupted' in some way.  Note that both NRG files can be mounted without problems with CDEMU, so the problem definitely seems to be with nrg2iso...

---

