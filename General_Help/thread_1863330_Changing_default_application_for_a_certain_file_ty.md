---
title: "Changing default application for a certain file type"
date: 2011-10-17
forum: General Help
---

### Post by hojjat on 2011-10-17
After installing Microsoft Office on Wine, I want .docx files to be opened by Microsoft Word by default. How can I set that configuration?

---

### Post by ajgreeny on 2011-10-17
Go to a docx file in nautilus and **right click ->properties ->Open with** tab and set it there.  You may need to use a custom command for the MS word, eg wine /home/user/.wine/path/to/word.exe or something similar.

At least, that is how I did it a long time ago with Lotus Smartsuite wps files that OOo did not open at that time.

---

