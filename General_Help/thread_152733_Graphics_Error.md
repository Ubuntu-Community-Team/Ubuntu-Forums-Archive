---
title: "Graphics Error"
date: 2006-03-30
forum: General Help
---

### Post by Keymaster on 2006-03-30
My graphics card doesn't work with Ubuntu, and X gives me an error saying no screens found.  I am using a Sony VAIO Laptop model VGN-FE550G.  The graphics card is an NVIDIA GeForce Go 7400.  All I can get into is the terminal, because X won't start.  How do I fix this?  (Please dumb it down for me if you can)

---

### Post by Ramses de Norre on 2006-03-30
sudo dpkg-reconfigure xserver-xorg
That should let you configure it properly, choose nv as driver, and if it still doesn't work then do it again and pick vesa. Vesa works with (quasi) all video cards, but you'll want to install the correct drivers then because vesa is really basic.

---

### Post by Keymaster on 2006-04-01
Thanks.  I hope this works.  Does vesa let you use S-Video?  If not, how do I find the correct drivers?

---

### Post by Sutekh on 2006-04-01
[Ubuntu Forums - HOWTO Latest NVIDIA Drivers]("http://www.ubuntuforums.org/showthread.php?t=75074")

 - Method 1 is very easy.  You can install the v7667 drivers from the Ubuntu repository

 - Method is a little more work to get the latest v8178 drivers.  Not too hard mind you, but not as simple as Method 1

---

