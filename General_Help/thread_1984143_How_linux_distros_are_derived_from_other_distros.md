---
title: "How linux distros are derived from other distros?"
date: 2012-05-21
forum: General Help
---

### Post by zealkaiser on 2012-05-21
Linux mint is derived from Ubuntu. Ubuntu is derived from debian. A lot of linux distros are dervied from some other distro. My question is how does they do that.

Many people answer me that they take the work of one distro and modify it for their. But this is not what I want to know. What I want to know is how they actually derive their work.
I want to know the technical process.

For instance suppose I want to build a minimal linux OS based on Ubuntu. Then what should I do?

---

### Post by Lars Noodén on 2012-05-21
You could try following these instructions if you are working from CD or, better, CD-RW:

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

Basically to make your own distro you start with an install or live image and add or remove or configure so drastically that it becomes a distro of its own.

Or instead of a CD, you could use PXE to serve the image and save LOTS of time.

---

### Post by oldfred on 2012-05-21
You can just start with minimal install. It is just about kernel and Internet to let you download only those packages you want.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
HowTo Achieve "Ubuntu-Desktop-Minimal" 
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

[]("http://andyduffell.com/techblog/?p=689")

---

### Post by xyzzyman on 2012-05-21
> **Lars Noodén said:**
> You could try following these instructions if you are working from CD or, better, CD-RW:

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

Basically to make your own distro you start with an install or live image and add or remove or configure so drastically that it becomes a distro of its own.

Or instead of a CD, you could use PXE to serve the image and save LOTS of time.

If you're just doing it for your own use, it'd take longer to set up a PXE server than to just use a USB drive... How many people still burn cd's?

---

