---
title: "Microprinting with Ubuntu"
date: 2012-09-06
forum: General Help
---

### Post by steveray100 on 2012-09-06
Way back in the MS-DOS days I had a little program that would microprint the contents of a floppy drive. It would print the files, with a little border around and then you could cut it out and glue it to the floppy. I would like to know if there is a program like this that will do it for all my CDs and DVDs.(Make a printout I can stick in the jewel case.) And if not, is there some way to do this using Terminal. (A bash script maybe)? Or a Windows program that someone knows of?

---

### Post by steveray100 on 2012-09-06
here is my crude solution if anyone is interested

cd dir_you_want_to_print

ls -C | lp -o "cpi=24"

---

