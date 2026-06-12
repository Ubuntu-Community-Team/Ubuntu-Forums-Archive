---
title: "HP Photosmart C4680 Driver Installation"
date: 2010-08-16
forum: General Help
---

### Post by Jaiichi on 2010-08-16
I recently purchased a new HP Photosmart C4680. I checked out my version of hplip (3.10.2) and it said the C4680 was supported by my version. So I thought: great, I'll just plug it in. So I start going through the setup.

It sees that my printer is from the C4600 series, and it asks me to pick the brand (which is auto-selecting HP) and then the printer model, which was auto-selecting PhotoSmart 7550; not even near my printer's model. I scan the whole list and my printer isn't in it. There was also a section of "PSC ####" printers, but none matched as well.

Is there an issue, or is the PS 7550 driver the expected driver to use with the PSC4680?

EDIT: It said it was supported since 3.9.6, but the release notes of 3.10.6 say it adds support for my printer, I'll try that. When I first tried to install it said gcc was missing, but I checked and it was there. It wanted C and C++ compilers so I added g++, I'm hoping that does the trick.

EDIT 2: Ok I got it working, I guess I shouldn't have trusted the documentation even though it was directly from hplip. Once 3.10.6 was installed it instantly found my printer.

---

