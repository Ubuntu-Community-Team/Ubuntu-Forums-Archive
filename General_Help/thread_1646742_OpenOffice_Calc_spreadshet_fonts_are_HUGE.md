---
title: "OpenOffice Calc spreadshet fonts are HUGE"
date: 2010-12-16
forum: General Help
---

### Post by HankB on 2010-12-16
When I create a new spreadsheet in OpenOffice Calc (3.2.1, on Ubuntu 10.10, 64 bit) The cells are nearly a half inch tall. The default font size is 10. If I go to Tools -> Options -> View I can reduce the Scaling value to about 70% and get a normal looking display, but then the menu fonts become really tiny. I can also change the font size to 6 and get a reasonable looking result, but I think this is more a kludge than a proper fix.

I checked for an environment variable that included DPI and can find none. 'xdpyinfo' reports:

```
...
screen #0:
  dimensions:    1600x1200 pixels (432x321 millimeters)
  resolution:    94x95 dots per inch
...

```
which seems right for my monitor.

I just opened a document in OO Writer and notice that the default font size is 12 and the result on the screen is much smaller than OO Calc (and looks normal.) It seems not to be a systemic problem but rather something with Calc itself.

Where is OpenOffice.org spreadsheet getting the idea to display the fonts in cells so large? 

Thank you for your help.

---

