---
title: "cups error_log &quot;Bad resolution&quot;"
date: 2011-04-11
forum: General Help
---

### Post by b1rdd0g on 2011-04-11
I have just installed Ubuntu 10.10, today, and I am having no small troubles with setting up a network printer. I followed the BoardDWorld HowTo for Brother printers (excellent!), and have managed to get the printer installed, however, I cannot get a Test Page to print. I have discovered errors in the cups error_log:

W [10/Apr/2011:23:02:27 -0500] Bad resolution "Fast0" for printer Brother-MFC-5840CN.
W [10/Apr/2011:23:02:27 -0500] Bad resolution "Normal0" for printer Brother-MFC-5840CN.
W [10/Apr/2011:23:02:27 -0500] Bad resolution "EnhNormal0" for printer Brother-MFC-5840CN.
W [10/Apr/2011:23:02:27 -0500] Bad resolution "Fine0" for printer Brother-MFC-5840CN.
W [10/Apr/2011:23:02:27 -0500] Bad resolution "Fine1" for printer Brother-MFC-5840CN.

I have no idea what these mean. I checked again to make sure that I had done a successful force install of the printer and cups drivers:

ii  cupswrappermfc5840cn                 1.0.2-3                                           Brother MFC5840CN CUPS wrapper driver
ii  mfc5840cnlpr                         1.0.2-1                                           Brother lpr Inkjet Printer Definitions

I would appreciate any help in diagnosing/correcting this issue. Thanks!

---

