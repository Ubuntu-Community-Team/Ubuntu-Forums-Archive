---
title: "Print fails from picasa"
date: 2009-07-19
forum: General Help
---

### Post by bmadaras on 2009-07-19
I am able to print from Open Office and Firefox but for some reason am not able to print at all from Picasa.  I get the printer may not be available message and after a certain about of time after submitting the print job from Picasa the printer is no longer listed as being connected via USB.

I have attached some logging.

hp-check.log is from the hp-check command run when the printer looks to be functional.

PrinterIssues.txt is a tail of /var/log/cups/*log so error and access, along with executing "lpstat -p && lsusb"

I can deal with having to work with my scanner from a Windows VM, but having to run Picasa in a windows VM is really going to start to annoy me since I use it so much more often

---

### Post by hyperdude111 on 2009-07-19
On the picaasa website this is stated. 

> A few print providers do not work correctly

This may be because picasa for linux is just the windows version running in wine and packaged with a .deb

---

### Post by bmadaras on 2009-07-28
That was my thought as well until I ran picasa with WINEDEBUG=1 and have no exceptions or errors listed, and Picasa reconiges my printer and interacts with it when I turned cupsd logging up to debug to change settings.

I am really just trying to find an error any place.  I printed from picasa to PDF printer successfully then to HP Photosmart unsuccessfully and did not see any difference in the WINEDEBUG log.

Can anyone let me know anything else I can do to turn up CUPS logging or the HPLIP driver logging so I can actually find an exception.

---

