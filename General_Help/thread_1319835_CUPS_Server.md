---
title: "CUPS Server"
date: 2009-11-08
forum: General Help
---

### Post by themagicmanfromtrent on 2009-11-08
My CUPS Server is seeing my printer, and has the correct drivers installed, but when I try to send it a job, although CUPS says that the job has been completed successfully, nothing happens... does anyone have any idea?

---

### Post by nikgare on 2009-11-08
Can you print a test page?
What printer is this, which Ubuntu version?

---

### Post by themagicmanfromtrent on 2009-11-08
No, the test page submits as a completed job, but doesn't print.

It's Ubuntu Server 9.04 x64. The printer is a Brother DCP-150C.

---

### Post by prem1er on 2009-11-08
What driver are you using?

---

### Post by nikgare on 2009-11-09
Have you installed the drivers from here?
[http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-DCP-150C](http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-DCP-150C)

Seems that you'll have to have a go at installing a proprietry driver from Brother, then it should work.

See also here: [http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793)

---

### Post by themagicmanfromtrent on 2009-11-12
Got it to work by installing ia32-libs.

Thanks!

---

