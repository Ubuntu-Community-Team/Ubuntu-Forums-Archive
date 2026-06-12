---
title: "Unable to copy to clipboard from Remote Desktop Viewer in 10.10"
date: 2010-10-19
forum: General Help
---

### Post by n2bnt2 on 2010-10-19
Just installed 10.10 32-bit on a Lenovo T61p laptop, and used Remote Desktop Viewer (version 2.3.2) to VNC into another system.

I can copy from an application on 10.10 and then paste into a window in the VNC connection (e.g. to xterm or emacs), but I cannot do the reverse. When I try to paste, I get garbage displayed.

For example, I selected "ls -l" from an xterm, which should have copied to the clipboard. When I paste this into an e-mail message, I get junk. Here is what Emacs in hexl-mode says about that text:

7852 3109 05                             xR1..

It shows as "xR1" some whitespace and then a tiny graphical box symbol with 00 and 05 in it. I'll try to paste it on the next line:


Is this a known bug? Is there a workaround? Another app I can use?
xR1    

This same VNC connection works fine, when I use 10.04.

Thanks!

PCM

---

### Post by eyrieowl on 2011-05-24
Obviously it's been a while...did you ever find a resolution for this?  I've been running into the same problem more recently.

---

