---
title: "Where has gedit gone?"
date: 2010-11-10
forum: General Help
---

### Post by petersull on 2010-11-10
Hi, I have several small text files containing simple short lists of information that I sometimes need to refer to quickly.

I created them with gedit which is ideal since it was so quick to open up and the user interface was not cluttered with menu bars and rulers etc.

Yesterday I found that all these little gedit files (7 of them in one folder) now open up with openoffice 3.2 which takes longer, presents me with an ascii filter options screen first, and the different formatting moves all the text around a bit so the information is less easy to read at a glance. Very annoying.

I checked and still have gedit installed but cannot seem to use it to open these files.

Is there a way to force these particular files to always open with gedit and still use openoffice for 'proper' word processing on other documents.

Best regards,

Pete.

---

### Post by mcduck on 2010-11-10
Sure, just right-click a file of certain type, select Properties and choose the program you want on the Open With-tab.

If you can't see Gedit there (it's listed as "Text Editor") click the Add-button and see if it's at least on that list. If it's not even there click the Custom command-button and set the command to /usr/bin/gedit

---

### Post by coffeecat on 2010-11-10
Do you mean open by double-clicking on them? If so, it sounds as though plain text files have become associated with OO. Right-click on a text file. What does the top line show - 'Open with Text Editor', or 'Open with OpenOffice'? If the latter, select 'Open with Other Application', make sure the 'Remember this application' box is ticked, scroll down to 'Text Editor', select this and open the file. After this all text files should be reassociated with gedit.

---

### Post by petersull on 2010-11-10
Thanks Mcduck and Coffeecat.

Got my simple gedit files back. :)

Cheers.

---

