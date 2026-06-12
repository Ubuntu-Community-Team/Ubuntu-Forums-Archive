---
title: "Sed replace 1-5 spaces"
date: 2010-09-12
forum: General Help
---

### Post by wesg on 2010-09-12
I have a .CSV file I need to clean up with bash. The csv file was built using OCR so the table row is all shown as 1 cell separated by xx spaces. I want to replace up to xx spaces with a single comma to start a cell. 

I've tried using ```
sed "s/[\s]{2,}//g"
``` but that doesn't seem to do the job. I replaced \s with just a " " character but that didn't fly either. 

Suggestions?

---

### Post by squaregoldfish on 2010-09-12
Is xx a specific number? If you just want to replace multiple spaces with a single space, the search string is:

s/  */ /g

(s/<space><space>*/<space>/g)

Steve.

---

### Post by wesg on 2010-09-12
90% of the lines have the same number of spaces, but I was hoping to encompass every possibility with 1 comma, so I don't have to check everything.

I've since made it work by replacing in series, but I'm still looking for the optimum thing.

---

### Post by squaregoldfish on 2010-09-12
I'm a bit confused - why won't the string I suggested work?
Some examples would be useful.

Steve.

---

