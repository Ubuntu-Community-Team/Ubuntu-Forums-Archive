---
title: "gedit malfunctions when invoked from launcher"
date: 2012-01-18
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2012-01-18
I made myself a drawer to help diagnose crashes. It has 2 launchers.

The first one has this command:
gedit /home/f/.xsession-errors

It works just as expected, opening that file with gedit.

The second has this command:
gedit /home/f/.xsession-errors-old

When I enter the same commands from a terminal the results are the same, i.e, .xsession-errors is read as expected but .xsession-errors-old for some reason shows as blank.

But when I use it, it SEEMS to open the correct file but it shows it as an empty file containing no text. But when I navigate to the directory with nautilus and open the file with gedit by right clicking on it the file has plenty of text in it, which is also confirmed by the file size as indicated by nautilus. This is the weirdest error I have ever encountered. Any ideas?

---

### Post by Wayne_V on 2012-01-18
perhaps you have some hidden characters in the second launcher command?

---

### Post by Dreamer Fithp Apprentice on 2012-01-18
mea culpa. Thanks for the reply. Sorry I posted and exposed myself for a fool. I had the file name wrong. Should have been a "." where I had a "-". Duh.

---

