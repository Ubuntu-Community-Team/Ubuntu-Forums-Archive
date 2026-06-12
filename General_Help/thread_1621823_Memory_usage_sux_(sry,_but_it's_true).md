---
title: "Memory usage sux (sry, but it's true)"
date: 2010-11-14
forum: General Help
---

### Post by Ctulhu on 2010-11-14
Hi all

I am using Ubuntu 10.10 64bit, fully updated etc. on two machines with each 3GB RAM, one with a 3-core AMD processor, the other with an Intel Core Duo. For a research project, I needed to handle a large tab-separated text file with 6 columns and approximately 600000 rows (approx. 85MB as txt, about 35.7MB as ods). This raised the following problems:

- it takes forever to open it in OpenOffice.org Calc and automatic column-wise replacements killed the system repeatedly - but when I do the exact same thing in my Windows 7 virtual box, which I gave 1.5GB of RAM, that takes about ten seconds and it's done. (Yes, this may be an OpenOffice.org thing, but still: Ubuntu provides this special OOO version (e.g., with the million rows thing so why not also fix this: what's the point of having 1E6 rows if you can't use them properly?)

- Then I want to copy and paste the file from a spreadsheet into a text file (the saving caused problems with text delimiters, don't ask). First, highlighting the whole data and press CTRL-C makes Ubuntu/OpenOffice go down for minutes; the virtual box with Excel doesn't even flinch, does it right away. Second, so I copy from Excel and want to paste into gedit. Doesn't do it for 2 minutes or so - in the virtual box, I open Notepadd++, paste it, 5 seconds later, done!

- Then I open the file in gedit for some cleaning up. Everything, like replacing double spaces by single ones, takes forever. Right now I have been waiting 10 minutes for a replacement of "\r\n" by "\n" and gedit is just dead in the water (yes, System Monitor says it's still working, but jeses, how long is that gonna take).

Seriously, I am the most ardent defender of open source etc. but this is ridiculous. I remember doing all this stuff on Win XP (I moved to Linux when Vista came) in no time at all, now, a few years later, with a computer that has 3 times as much RAM as I had back then, and a brand new open source OS, I have to go back to some frakking virtual box with Windows 7 to get some text processing and spreadsheet stuff done?? What can one do to avoid these kind of issues??

---

