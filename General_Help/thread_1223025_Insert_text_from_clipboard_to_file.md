---
title: "Insert text from clipboard to file"
date: 2009-07-25
forum: General Help
---

### Post by Chamillionaire2 on 2009-07-25
What's Up?

Is their a way I could insert the text in the clipboard to a file? And to a specific line?

Thanks Bye.

---

### Post by hetx on 2009-07-25
Ehm, opening the file in a text editor and pasting?

---

### Post by ajgreeny on 2009-07-25
What have you tried so far?  It's exactly the same in ubuntu as in windows, put the cursor where you want it and paste.  Get parcellite and you can have multifill clipboard, with up to 100 entries remembered even after a reboot.

---

### Post by Chamillionaire2 on 2009-07-26
I forgot to mention, Via some automated way, not by simply pasting in the text file manually.

---

### Post by ajgreeny on 2009-07-26
Explain more please; I haven't got a clue what you mean.

---

### Post by DaithiF on 2009-07-26
not entirely clear either on your requirements, but possibly you want xclip

sudo apt-get install xclip

then
xclip -o > somefile

will write contents of clipboard to somefile.

---

