---
title: "Video problems after upgrade"
date: 2010-10-01
forum: General Help
---

### Post by pan69 on 2010-10-01
Hi,

During the week I did a update through the update manager and since then my video has been broken.

I usually just quickly glance through the list of packages to be updated before pressing install and this time I notice that a component called fglrx was going to be updated. I can only speculate that this has anything to do with it.

After the update I did a reboot and that's when the trouble began. My system was unable to boot into high resolution mode and gave me the option to boot into low graphics mode or reconfigure. I fiddled around a bit and after a while I was able to get back to a low-res desktop.

The first thing I did was seeing if my hardware drivers where still enabled so I opened the System / Administration / Hardware Drivers panel and after searching for available drivers it came up with an empty list. I downloaded the latest ATI x86_64 drivers and did an install of those. Installation was successful and I did a reboot.

I've tried a 'sudo dpkg-reconfigure xserver-xorg' but this seem to do nothing. It just drops back to the command-line without a message.

I'm currently in high-res mode but I don't seem to have any hardware acceleration. Dragging a window around the desktop is a painful to watch process. There is an aticonfig command line utility that outputs about 50 zillion options. I'm pretty sure there used to be a graphical UI version of it but I can't seem to find it anywhere in my Applications menu.

I'm currently on Ubuntu 9.10 (haven't had time yet to upgrade) and I have an ATI Radeon 5450 video card.

Any help would be greatly appreciated.

**UPDATE**
When I issue the following command: fglrxinfo I get the following output:

```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  15
  Current serial number in output stream:  15
```

---

