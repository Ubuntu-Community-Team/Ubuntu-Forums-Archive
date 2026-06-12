---
title: "Abiword default template"
date: 2010-08-27
forum: General Help
---

### Post by Ubunthree on 2010-08-27
I am unable to persuade AbiWord to recognize my changes to the normal.awt template. I think I've figured out what's going on, but don't know how to fix it.

AbiWord's documentation says that the default font etc. is defined by the file:

/home/username/.AbiSuite/normal.awt

If I click on this file, AbiWord starts up with my custom defaults set as expected. However, AbiWord appears not to read this file at startup or for new documents. It actually reads this file:

/usr/share/abiword-2.8/templates/normal.awt

AbiWord is unable to save the template here, probably due to permissions, so you have to save it to the /home/blabla location and then go in as root and manually copy it to the /usr/blabla directory. This works, but is obviously very awkward.

Is there a way to either A) make AbiWord *load* the template from my home folder as it is supposed to, or B) enable and direct AbiWord to *save* the template into the same /usr/blabla folder that it loads from? Option A would be preferable of course.

Thank You!

---

