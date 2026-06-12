---
title: "Encrypt the file list too!"
date: 2010-05-19
forum: General Help
---

### Post by Rytron on 2010-05-19
Hi.
I use this line to line to archive and  password protect my files (with zero compression):
[COLOR="Indigo"]7z a -p -t7z -mx0 ~/Documents.7z ~/Documents[/COLOR]

In the attached picture, I notice there is a check box to 'Encrypt the file list too' via the GUI 7z method. How could I add this option to the above 7z line?

Also I think rar allows you to 'Encrypt the file list too'. Could someone also give me a rar line similar to [COLOR="Green"]7z a -p -t7z -mx0 ~/Documents.7z ~/Documents[/COLOR] but that has the 'Encrypt the file list too' feature added?

Thank you.

---

### Post by Rytron on 2010-06-11
Got it!

7z a -p -t7z -mx0 -mhe=on ~/Documents.7z ~/Documents

---

### Post by KingYaba on 2011-01-09
> **Rytron said:**
> -mhe=on

Thank you very much. This is what I have been looking for.

---

### Post by Rytron on 2011-01-09
> **KingYaba said:**
> Thank you very much. This is what I have been looking for.

No problem KingYaba, you are welcome.

---

