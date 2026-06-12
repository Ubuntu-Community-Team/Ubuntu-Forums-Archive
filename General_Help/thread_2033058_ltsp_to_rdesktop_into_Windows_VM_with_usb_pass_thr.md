---
title: "ltsp to rdesktop into Windows VM with usb pass through"
date: 2012-07-25
forum: General Help
---

### Post by greavette on 2012-07-25
Hello,

I'm looking at setting up a thin client terminal that connects to my ltsp server.  Once into an ubuntu desktop I'll need rdesktop to connect to my Windows VM.  Connected to the thin client will be a keyboard, mouse, usb hand scanner and usb weight balance.

Will I be able to pass through these usb devices through rdesktop to my windows VM?  Does it 'just work' or do I need to use special software to assist?

Or should I forget about the ltsp server, run linux (ubuntu) on a small client PC that automatically boots into rdesktop to my Windows VM?  Would this work better?

Thank you.

---

### Post by Cheesemill on 2012-07-25
There's no need to boot to Ubuntu first and then fire up an RDP connection when you can connect directly to an RDP session from LDM (the LTSP login screen).

For details just search the documentation for rdesktop.
[http://sourceforge.net/projects/ltsp/files/Docs-Admin-Guide/LTSPManual.pdf/download](http://sourceforge.net/projects/ltsp/files/Docs-Admin-Guide/LTSPManual.pdf/download)

Other info available here:
[https://help.ubuntu.com/community/UbuntuLTSP/RdesktopLocaldev](https://help.ubuntu.com/community/UbuntuLTSP/RdesktopLocaldev)

---

### Post by greavette on 2012-07-25
Thanks very much for the reply.

This is partly what I need.  Good to know that I can connect directly to an RDP session from LDM.  I will review your links!

What about usb devices being available from the thin client, passing into my ltsp session and being redirected to my Windows VM?  Doable or wrought with problems?

Maybe instead of rdesktop I should look at FreeRDP?

---

