---
title: "Ubuntu Software Center Issue...Stalls"
date: 2010-10-18
forum: General Help
---

### Post by roystreet on 2010-10-18
Hello,
...The software center appears to stall on me.  I am able to open software center & even search for software to install.  When I select one to install, it then requests a password to authenticate. I input the password, then dialog box where I input the password stays opens, (no password failures) then button that states "authenticate" stays visible, but I don't see any status. It "appears" to be downloading files, but once again, it doesn't show the status. After awhile it seems to fail.
.
The whole OS doesn't freeze.  If I open synaptic & select software to install, it completes the process quickly & efficiently.  It requests a password (As it should) & then goes on it's merrily little way doing what it should right away!
Anyone having the same issue?
~roystreet

---

### Post by roystreet on 2010-10-18
I want to add to this issue that I've noticed when I have to authenticate even when changing the default monitor it will allow me to enter the password, then I press authenticate...Then the authenticate box just stays open & the change isn't made.

Maybe it's an authentication issue & not a software center issue.

I've attached the example I have concerning the multi-monitor issue.  I've left it open for maybe 5-10 minutes & it stays exactly this way.  Just to reiterate...This happens even when using the software center, so I don't see how it has anything to do with monitor support.

thanks

Adding more information:
I've noticed now that once I input the password to authenticate & it "freezes" as I've mentioned...If I close the dialog box requesting the password, it appears to then download & install software.  Or in the image I've added, it then will update the monitor settings once I close out the box.

Any ideas on this one?

---

### Post by roystreet on 2010-10-21
Well does anyone have any thoughts or suggestions on this at all? :confused:

No thoughts? - Come on...Someone has experienced this before...Am I the only one? :)

---

### Post by ratman1 on 2010-10-22
Same thing happening here...

The bug has been reported though, and in the meantime just wait and keep checking for updates.

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/649939](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/649939)

Also, i found that if you put a force quit button on one of your panels, you can quit the frozen authentication window and re-try the password, though make sure you CLICK the authenticate button (not by pressing enter/return on your keyboard). Sometimes that works. Sorry i couldn't help too much, but the bug should be fixed soon. :)

---

### Post by roystreet on 2010-10-22
Thank you very, very much for your response.  It was very helpful to me.  Plus a comfort knowing that this issue is being addressed.

~roystreet :)

---

