---
title: "Problem installing bought game in Software center"
date: 2012-06-03
forum: General Help
---

### Post by Diskdoc on 2012-06-03
Having trouble with Software center segfaulting when trying to install a game from the Humble Bundle. Saw it working well another computer with Ubuntu 12.04. I approve the terms and conditions, it says something akin to "Connecting to payment service"...aaand..crash. This the output from terminal:

> mickeuser@micke:~$ software-center
2012-06-03 14:01:55,791 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-06-03 14:01:55,811 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-06-03 14:01:56,568 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-06-03 14:01:57,179 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2012-06-03 14:02:15,701 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0
2012-06-03 14:02:15,706 - softwarecenter.db.database - INFO - reopen() database
2012-06-03 14:02:15,706 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True

(software-center:5211): Pango-CRITICAL **: pango_font_description_set_size: assertion `size >= 0' failed

(software-center:5211): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'DejaVu Sans'

(software-center:5211): Pango-WARNING **: font_face status is: no error has occurred

(software-center:5211): Pango-WARNING **: scaled_font status is: invalid matrix (not invertible)

(software-center:5211): Pango-CRITICAL **: pango_font_description_set_absolute_size: assertion `size >= 0' failed
Segmenteringsfel (minnesutskrift skapad)
mickeuser@micke:~$


What to do?

---

### Post by Paddy Landau on 2012-06-03
I would report a bug for this.

Do you know if it took your payment, or did it fail before the payment was collected?

---

### Post by Bucky Ball on 2012-06-03
Maybe look into installing pango, if that is possible. Just had a look in synaptics and there seems to be packages. Maybe it need pango ...

---

