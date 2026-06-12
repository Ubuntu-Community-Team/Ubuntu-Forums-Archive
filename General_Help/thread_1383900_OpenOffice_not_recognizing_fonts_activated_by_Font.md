---
title: "OpenOffice not recognizing fonts activated by FontMatrix"
date: 2010-01-17
forum: General Help
---

### Post by vamega on 2010-01-17
I activated a bunch of fonts through FontMatrix, which is a font manager I installed from the Ubuntu Software Center. The Font's were then available to me in inkscape, and a bunch of other programs. Now however I wanted to use some of those fonts in OpenOffice Impress (Presentation), but OpenOffice didn't seem to list the fonts.

Does anyone know how I can solve this. I'm assuming that one of two things is happening. Either OOo is not following the symlinks that are present in the .fontmatrix directory, or that openoffice is hard coded to not read fonts from any directory other than .fonts.

Vamega

---

### Post by warfacegod on 2010-01-17
Check the OOo preferences window. OOo uses the ttf-corefonts I nstalled with Synaptic just fine.

---

### Post by vamega on 2010-01-18
> **warfacegod said:**
> Check the OOo preferences window. OOo uses the ttf-corefonts I nstalled with Synaptic just fine.

I installed the MS fonts through synaptic, and that worked just fine. However it doesnt seem to discover fonts installed in my home directory in either the .fonts directory, or the .fontmatrix directory.

I finally figured out why it didn't install any of these fonts. It was simply because they were opentype fonts and openoffice didn't support opentype fonts, something I had taken as a given, because so many programs implement it just fine.

Sadly now I'll have to go back to MS Office, until OOo can finally give me a feature I really need, can't wait to 3.2 is finally released, I hear that it had Opentype support.

---

