---
title: "vi error message"
date: 2012-02-07
forum: General Help
---

### Post by fra11 on 2012-02-07
Hi all, 
after forcing closure on vi now I'm getting this strange error message
E297: Write error in swap file    
accordingly to other forums the problem is that I don't have any more space but it is only due to the fact that I forced closure on vi before. 
Can anyone help me out?
Thanks:confused:

---

### Post by squaregoldfish on 2012-02-07
vi keeps a swap file of each file it edits - for example, if you edit "file.txt", it will create a file called ".file.txt.swp". These files will normally get deleted when you quit vi, but if you killed it, it will still be around. Normally you're warned about this when you try to edit the file again, but perhaps vi is upset in some way. Anyway, look for the swap file, and if it's there delete it. All should be well after that.

Steve.

---

### Post by fra11 on 2012-02-07
Thanks Steve. I was looking for the file but apparently it doesn't exist, so maybe I really had run out of space on disc, even though it sounds so strange... mah!
Thanks anyway...
Fra

---

### Post by Khayyam on 2012-02-07
fra11 ...

squaregoldfish is correct, just remove the .file.swp and you'll be back to normal. However, you can revover any lost changes using the .swp. This is is a case of "101 Reasons for using vim over vi" .. vim will automatically ask you if you want to [recover changes from a swap]("http://vimdoc.sourceforge.net/htmldoc/recover.html") and not simply spit out a "strange error message".

HTH ..

---

