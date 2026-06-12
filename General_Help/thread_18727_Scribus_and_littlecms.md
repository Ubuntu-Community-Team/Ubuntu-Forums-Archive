---
title: "Scribus and littlecms"
date: 2005-03-08
forum: General Help
---

### Post by watchitman on 2005-03-08
Anyone know how to make thses two work together on Ubuntu? As it is, littlecms is installed but the color management option doesn't show up in Scribus.

---

### Post by kperkins on 2005-03-15
I have the same question.
Anyone?
I'm still checking into it, but any help would be appreciated.

---

### Post by kperkins on 2005-03-15
Got it figured out.
Go to the Adobe site and download the ICC profiles: [http://www.adobe.com/support/downloads/thankyou.jsp?ftpID=2348&fileID=2244](http://www.adobe.com/support/downloads/thankyou.jsp?ftpID=2348&fileID=2244)
Extract them into  a folder (/usr/share/scribus/profiles) is good (/usr/share/scribus should already be there.) (just the.icc files--I extracted the Adobe .zip my home folder, and copied just the .iccs  to that folder) 
Open scribus and go to Settings > Preferences > General  There's a box under Paths to enter the path to icc profiles.  Enter the path there.  Hit ok.  Go back to Setting > Color Mangement.  Enable color management.
Should be good to go.

---

### Post by shongzah on 2007-03-29
I couldn't get the Adobe download to work but it looks like the Scribus folks have a stash.

get it here->[Scribus downloads]("http://www.scribus.net/modules.php?op=modload&name=Downloads&file=index&req=viewdownload&cid=16")

---

### Post by shongzah on 2007-03-29
Scratch that.  It's an RPM file.  I did find the [Adobe files though]("http://www.adobe.com/support/downloads/product.jsp?product=62&platform=Windows")

---

### Post by juanJosepablos on 2007-12-14
Just for the record on ubuntu 7.10:

aptitude install icc-profiles

---

### Post by Thorndeux on 2008-06-07
You have to close all documents, then the Color Management entry shows up in the preferences.

---

