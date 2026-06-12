---
title: "determining max resolution of TV?"
date: 2012-09-18
forum: General Help
---

### Post by princeofnam on 2012-09-18
for whatever reason my TV via VGA tells my g7-1070us laptop that its max resolution is 1024x768.  I somehow doubt this from the level of blurriness when I set it to this max resolution. I'd like to override this via xrandr but I don't know what the actual max resolution of the TV is.  I've tried some random resolutions like 1366x760 but I often get a black screen when I try.  The TV is a lg 42pc3dv.  Is there any systematic way of approaching this issue?

---

### Post by f8l_0e on 2012-09-18
[http://www.hdtvsolutions.com/LG_Electronics-42PC3DV.htm](http://www.hdtvsolutions.com/LG_Electronics-42PC3DV.htm) claims that the native resolution is 852x480

[http://www.lg.com/us/support-product/lg-42PC3DV-UE#]("http://www.lg.com/us/support-product/lg-42PC3DV-UE#") has the product manual.

It lists the following (the lines with the * are only available over vga-connector):

*640x350 31.469 70.08 
640x480 31.469 59.94
*720x400 31.469 70.08
800x600  37.879 60.31
1024x768 48.363 60.00
1280x768 47.776 59.87
1360x768 47.720 59.799
1366x768 47.130 59.65

I would try 720x400 for best clarity. You will have black borders around the image unless you adjust overscan or use a zoom feature. 

720x480 is available over HDMI2 which I would really suggest that if you have HDMI or DVI on the computer. 
This will leave black borders on the left and right of the image.

In either case, as this is a plasma screen, DO NOT, leave the screen on displaying a still image it WILL burn in.

---

