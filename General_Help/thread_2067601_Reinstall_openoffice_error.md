---
title: "Reinstall openoffice error"
date: 2012-10-07
forum: General Help
---

### Post by cmr77 on 2012-10-07
Sorry to drag this one out of the woodwork, but have tried all of the above and still not getting anywhere.

I am a complete newbie, any help would be much appreciated.

Cheers

---

### Post by jerrrys on 2012-10-07
Hi cmr77, welcome to the forums  :)

Do you mean libreoffice?

---

### Post by PaulW2U on 2012-10-07
cmr77, I see that you originally posted here - [http://ubuntuforums.org/showpost.php?p=12282213&postcount=7](http://ubuntuforums.org/showpost.php?p=12282213&postcount=7) and your post was [s]moved[/s] copied here as you responded to an old thread.

It's probably best to now clarify if you really want to reinstall OpenOffice or not. LibreOffice is what is now supported on the newer releases of Ubuntu.

---

### Post by jerrrys on 2012-10-07
I see

OK, [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

gksudo nautilus

Go to your filesystem then do a search on openoffice and manually remove all leftover files.  Then repeat this for libreoffice.  Then install your choice (recommend libreoffice).

Next time you want to do something like this that requires removal of prior package, use the [purge command]("https://help.ubuntu.com/community/AptGet/Howto#Removal_commands").

Any questions ?

EDIT:  Be careful when using sudo.  Any file deleted while in sudo (gksudo) is gone, gone, gone  :)  no turning back

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cmr77 on 2012-10-07
Thanks for responding guys...I originally wanted to try libreoffice, but read time and again to remove openoffice first.  And now can't get either to install...

Am running Ubuntu 10.04 on an aging Macbook. 

Will try above and get back to you!
Cheers

---

### Post by cottfcfan on 2012-10-07
Try...
```
sudo apt-get purge openoffice*
```
then
```
sudo apt-get purge libreoffice*
```
then
```
sudo apt-get install libreoffice
```
If you encounter any errors post them back here.

---

### Post by cmr77 on 2012-10-07
Had tried above and have completely messed up. Thanks for help though! Am trying to reinstall as had errors I didn't understand! Oops, should leave well alone!

---

### Post by jerrrys on 2012-10-07
Post the errors please

---

### Post by cmr77 on 2012-10-07
terminal wouldn't "exit", went to restart but it wouldn't. Sorry should have noted it all down, next time eh!

---

### Post by Hagar Delest on 2012-11-15
You can install AOO  and LibO with the .debs downloaded directly from the official web sites. Note that this way you can install and run both applications in parallel. But you need to remove the packages coming with the Ubuntu out of the box configuration first.

See: [[Ubuntu] Installing OOo on Debian and Co.](http://forum.openoffice.org/en/forum/viewtopic.php?f=74&t=68)

---

