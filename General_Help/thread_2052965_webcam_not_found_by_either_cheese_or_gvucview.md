---
title: "webcam not found by either cheese or gvucview"
date: 2012-09-04
forum: General Help
---

### Post by jlh68 on 2012-09-04
It worked and now the webcam seems not to exist.  Neither gvucview or cheese can find the built in webcam.  I get a message that the webcam is not connected or the driver is missing.

How does a driver dissapear?

How do I get the webcam to work again?

---

### Post by jlh68 on 2012-09-04
Some additional infromation:
> john@Nighthawk:~$ ls /dev/video*
ls: cannot access /dev/video*: No such file or directory
john@Nighthawk:~$ vlc v4l2:///dev/video0
VLC media player 2.0.3 Twoflower (revision 2.0.2-93-g77aa89e)
[0x7f9a8c0010c8] v4l2 demux error: cannot open device '/dev/video0': No such file or directory
[0x7f9a8c004cf8] v4l2 access error: cannot open device '/dev/video0': No such file or directory
[0x7f9ab0000b78] main input error: open of `v4l2:///dev/video0' failed


where did video0 go?  It seems to have didapeared.

---

