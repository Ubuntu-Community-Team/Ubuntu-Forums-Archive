---
title: "Dual monitors revert to single after every logout"
date: 2009-11-07
forum: General Help
---

### Post by dbc001 on 2009-11-07
Fresh install of Ubuntu 9.04 x64, using nvidia with the 180 restricted drivers. I can set up dual monitors with twinview using the nvidia applet, but every time I log out it resets back to a single monitor setup.  Then I have to start over.  This happens whether or not compiz is enabled.  It's not a laptop - the monitors never change.  How can I get my dual monitor settings to stick?

thanks in advance,
dbc001

---

### Post by scouser73 on 2009-11-07
Please follow these instructions for setting up dual monitors.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - **X Server Display Configuration** will now start, now you can set up your monitors to your liking

**3** - Once you have done so click **Apply** then click **Save To X Configuration File**

You will now have dual monitors working.

---

### Post by dbc001 on 2009-11-07
Thanks! That worked perfectly.

---

### Post by scouser73 on 2009-11-07
Glad to help mate, can you mark this as being solved now please.

---

### Post by Foxcow on 2009-12-10
Fantastic.  I can never remember this.

---

### Post by Bartender on 2009-12-26
Wish I'd read this thread first.  I was having the same problem, finally realized that the 180 application wasn't saving the new xorg setup, so I manually copy/pasted the xorg file after getting the monitors set up how I wanted, and replaced the default xorg.  That worked, but this sounds better.

---

