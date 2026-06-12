---
title: "Citrix woes?"
date: 2010-02-17
forum: General Help
---

### Post by mma8x on 2010-02-17
ok, so i've been wrestling with citrix/xenapp client for a while, and i think i ALMOST have it figured out.  i have 2 usb drives with karmic, one running 64 bit and one using 32.  i have wfcmgr running on both now.  32 bit was fairly easy--only needed a symlink from libXm.so.3 --> libXm.so.4.  64 bit was a bit trickier; i installed the 32 bit motif libs as detailed in other threads, did the symlink as above.  also needed to install the ia32-lib package, which i didn't see mentioned anywhere else. now both installations run this test site ok:
[https://dcm.toolwire.com/training/jsp/ui/moat_readiness.jsp](https://dcm.toolwire.com/training/jsp/ui/moat_readiness.jsp)

another trick that i didn't see anywhere else: on both installations, when i click on the web interface application, nothing would happen.  about:plugins showed npica.so as being the application.  i removed this file from the plugins directory.  then i click on the app, and firefox asks what to do with the .ica file, and i choose open with wfica.  so this worked great with the 32 bit install.  64 bit, i still get nothing.  firefox doesn't ask what i want to do with the file.  if i go the the test site above, it does ask me what to do with the ica; i chose open with/do this everytime using wfica.  again, this works on the test site, but not on my company site--still just opens a blank window.  so i don't know if this is a 64 v. 32 bit issue, or what.  any ideas?

---

### Post by mma8x on 2010-03-01
a bit of an update.  i had still been struggling with this; despite being able to open wfcfmr without a problem, i ran FF from a terminal and got:
```
LoadPlugin: failed to initialize shared library /home/ubuntu/ICAClient/linuxx86/npica.so [/home/ubuntu/ICAClient/linuxx86/npica.so: wrong ELF class: ELFCLASS32]

```

so it looked like i still had some 64 bit issues.  i installed nspluginwrapper, and did like so:
```
nspluginwrapper -i ~/ICAClient/npica.so
```
results:
```
nspluginwrapper -l
/home/ubuntu/.mozilla/plugins/npwrapper.npica.so
  Original plugin: /home/ubuntu/ICAClient/linuxx86/npica.so
  Wrapper version string: 1.2.2

```

that still didn't work, until i removed npica.so from the plugins directory.  now all works well.  i think that the install script installs npica.so automatically, and then FF preferentially tries to load that one, even if nspluginwrapper is installed...HTH.

---

