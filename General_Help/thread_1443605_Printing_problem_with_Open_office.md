---
title: "Printing problem with Open office"
date: 2010-03-31
forum: General Help
---

### Post by pravindra.kumar on 2010-03-31
Hi,
I have installed Open office.org 3.0 and now i am facing printing problem with my documents. In print preview it's showing margins properly but after giving print command print out comes with 0.00" margin, first row of calc/word file is almost missing on paper.
Printer model is HP Laserjet 1160 and Operating System is Xubuntu 9.04 and paper size is 8.27"x11.69".
I am unable to find the way how to fix the problem.

Please help me.
Thanks

---

### Post by pravindra.kumar on 2010-04-01
The above problem has been solved by doing the following:-
# Download the attached pstopdf and install it in /usr/lib/cups/filter/
cd /tmp
wget [http://launchpadlibrarian.net/25537150/pstopdf](http://launchpadlibrarian.net/25537150/pstopdf)
sudo cp pstopdf /usr/lib/cups/filter/
# Then change the permissions of the installed file:
sudo chmod ugo+rx /usr/lib/cups/filter/pstopdf

Thanks

---

