---
title: "open .csv files with KWordQuiz via Nautilus"
date: 2012-08-06
forum: General Help
---

### Post by Bazon on 2012-08-06
open .csv files with KWordQuiz via Nautilus seems not to be possible: even with the expanded view of the "open with" dialogue, KWordQuiz is not mentioned. 

I tried to change that by editing the /usr/share/applications/kde4/kwordquiz.desktop file by changing the line 
```
MimeType=application/x-kvtml;
```
to
```
MimeType=application/x-kvtml;application/csv;
```
but it didn't help.

Has anyone another idea?
thanks!

---

### Post by mc4man on 2012-08-06
Don't have any such files but have you tried - 
MimeType=application/x-kvtml;text/plain;

---

### Post by Bazon on 2012-08-06
Thanks, I added that (so the line is now ```
MimeType=application/x-kvtml;application/csv;text/plain;
```), restartet nautilus with ```
nautilus -q
```, but it didn't help: KWordQuiz isn't in that list. :-(
(although almost every other application is...)

---

### Post by mc4man on 2012-08-06
It would appear it's being prevented from showing in nautilus because the Exec= ends with %i
I know nothing about this app, nor about .cvs, ect.

You could try adding a %f after the %i & see what happens.... (have a space between %i & %f

Edit - 
[http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html)
the %i is described there, whether you need it ??, if not replace with %f or %U or %u

---

### Post by Bazon on 2012-08-06
Yes, adding %f solved it, thanks! :-)
(restarting nautilus wasn't even necessary.)

---

