---
title: "XSane crashes, the default device is invalid"
date: 2009-09-07
forum: General Help
---

### Post by crazyfuturamanoob on 2009-09-07
I have Canon LiDe25 flatbed scanner. It works and is 100% usable from command line.

But XSane will fail at start, and report an error: "Failed to open device v4l:/dev/video0, invalid argument.", and exit.

v4l:/dev/video0 is my laptop's built-in webcam, which I never use, and it does not have proper drivers, so it doesn't even work.

I want to get XSane working, so I must set the default device as the scanner (plustek:libusb:004:003).

What configuration files I need to edit and how? Or can I make the webcam invisible for XSane and my system?

---

