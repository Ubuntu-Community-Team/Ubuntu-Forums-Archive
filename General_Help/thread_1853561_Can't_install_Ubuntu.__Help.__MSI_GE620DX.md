---
title: "Can't install Ubuntu.  Help.  MSI GE620DX"
date: 2011-10-02
forum: General Help
---

### Post by Colby3316 on 2011-10-02
I keep getting this error when install Ubuntu.  I tried installing BackTrack and I got the same thing but I went down to the 4th setting the says Default No Text or something.  It looks the same as the first but it worked.  They do not have the setting on regular Ubuntu 11.04.  I have an MSI GE620DX.  Please help.

[IMG]http://i.imgur.com/zcWBV.png[/IMG]

---

### Post by Blasphemist on 2011-10-02
I do believe you have a some "stuff" ahead of you. You have nvidia/intel optimus graphics. You'll need to do some kernel mode setting to get past this installation error and then further kernel mode setting to the installed grub2. [http://ubuntuforums.org/showthread.php?t=1758080](http://ubuntuforums.org/showthread.php?t=1758080)
Forum user DanielBuus seems to have it right in this thread.

Then you need to implement ironhide. [https://launchpad.net/~mj-casalogic/+archive/ironhide](https://launchpad.net/~mj-casalogic/+archive/ironhide) and [http://axel668.wordpress.com/2011/08/25/ironhide-nvidia-ion2-support-for-buntu/](http://axel668.wordpress.com/2011/08/25/ironhide-nvidia-ion2-support-for-buntu/)

There would be a lot of steps to document here so try to do this and post any questions you have.

---

