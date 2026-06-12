---
title: "Libreoffice Forms toolbars missing"
date: 2011-02-08
forum: General Help
---

### Post by cscj01 on 2011-02-08
I just installed Libreoffice from the PPA.  Now, I cannot activate any toolbars from the View menu, so I do not have the Form Design nor the Form Control toolbars.   These are Base Forms.

Any ideas?

I have been able to get the toolbars to display by doing the following:

Display form in fullscreen mode;
Revert back to normal display;
View>Toolbars>Form Design>Check;
Repeat above for Form Navigation and Form Controls.

The problem is even though I then save the form, I have to do it all over again when I re-open the form.  Also, some of the icons, such as Form Navigator, are not active.  I had initially installed Libreoffice from the debs, and I did not have this problem.  After checking to see if all my forms worked properly, I decided to go ahead and install from the PPA.  I removed the original deb install, added the PPA repository, and installed.  Now it seems I have a mess.  I suppose I'll have to remove Libreoffice, delete the PPA repository, re-install OOo, then re-install Libreoffice from the debs.  Hopefully, I'll be able to work again.

---

### Post by cscj01 on 2011-02-08
Okay, I removed Libreoffice, deleted the PPA repository, re-installed OOo (after using Ubuntu Tweak to get rid of everything), re-installed Libreoffice from the debs, and all is working again.  It makes no sense to me why the PPA install did not work properly except to assume there is something wrong with that procedure.

---

### Post by linuxyeti on 2011-02-10
Hi

I agree, after leading myself down numerous dark alleys.

The stock install of LibreOffice works fine, unless of course your screen resolution is less than 1024x768.

Which, of course, seems extremely odd if you ask me. Ubuntu is installed on many netbooks, and yet, a key application, simply won't work on it, resolution tends to be (1024x576).

I think it's really important, that the resolution limitation is resolved as soon as possible, and certainly before LO replaces OO3.2 as the default install.

OO 3.2, has no such issues with regards to resolution on netbooks.

I can confirm, OO 3.3, exhibits the same behavior as LO 3.3.

---

