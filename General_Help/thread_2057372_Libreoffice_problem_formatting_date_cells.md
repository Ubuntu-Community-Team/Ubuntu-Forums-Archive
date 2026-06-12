---
title: "Libreoffice problem formatting date cells"
date: 2012-09-13
forum: General Help
---

### Post by lumaja on 2012-09-13
[COLOR=black][FONT=Bitstream Vera Sans]I copy into Libreoffice Calc from web site a table with dates, clinking on the cells with dates redirects to the same web site and can’t be formatted. How to format this dates.[/FONT][/COLOR]
[COLOR=black][FONT=Bitstream Vera Sans]Thank you [/FONT][/COLOR]

---

### Post by Vaphell on 2012-09-13
instead of ordinary 'paste' which preserves source formatting try 'paste special' option. Select 'plain text' and use tab as column delimiter to parse data into proper columns. It should strip all formatting.

---

### Post by kimberlite on 2012-09-13
Ctrl+M removes all direct formatting including hyperlinks beside Vaphell solution.

---

### Post by lumaja on 2012-09-14
Thank you for such quick response.
 

 Following the two suggestions.  
 The dates cells becomes text (') on deleting the *apostrophe **becomes date 05/09/12 which is correct but formatting to* “*1 Jan 2004” *becomes 12 Sep 2005 it changes the day to year.
 Can I do anything about this?

---

### Post by vasa1 on 2012-09-14
> **lumaja said:**
> Thank you for such quick response.
 

 Following the two suggestions.  
 The dates cells becomes text (') on deleting the *apostrophe **becomes date 05/09/12 which is correct but formatting to* “*1 Jan 2004” *becomes 12 Sep 2005 it changes the day to year.
 Can I do anything about this?

While pasting, look for "Detect Special Numbers (such as dates)" and tick that box.

Edit: here's an image.

---

### Post by vasa1 on 2012-09-14
Another way to deal with the ' which seems to be common when getting stuff from several financial sources, there's a *post facto* trick I learned over at the [openoffice.org site]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=9&t=26626&p=121627#p121137").

Select the whole sheet or specific cells, then press Alt+E,L to get the search / replace window. In the search box type ```
.+
```
In the replace box, type ```
&
```
Before hitting enter make sure that "use regular expressions" in ticked under "more options".

---

### Post by lumaja on 2012-09-16
To Vasa1 how to open the attached Thumbnails. Clinking on it another window opens with  
 “*Select the language to use for import” *but window freezers.
 Thank you to wall for the suggestions but I tried all time and time again and the conclusion is the same “12 Sep 2009”, day becomes year and year becomes day.
 After Format>Clear Direct Formatting the dates are correct but are text (') delete the (') a figure becomes date but if just change the format or make any calculation like =A5+1 it changes to what I explain above.
 

 Just for information Excel 2000 can do this very easy the same in Gnumeric, I can’t see why in Libreoffice and Openoffice is so difficult, sorry this is just a newbie point of view.
 

 I regard all of you with great respect to help us with our difficulties.

---

### Post by vasa1 on 2012-09-16
What thumbnail are you referring to?
What version of LibreOffice are you using?
What are your Language Settings? Tools, Options, Language Settings, Languages.
What do you have under Format, Cells, Numbers?
Please put up screenshots that provide the information.

> Just for information Excel 2000 can do this very easy the same in Gnumeric, I can’t see why in Libreoffice and Openoffice is so difficult, sorry this is just a newbie point of view.

Let's not start debating this or your thread will turn into something very different :)

---

### Post by lumaja on 2012-09-17
What thumbnail are you referring to?  **On your post #5 ** 
 While pasting, look for "Detect Special Numbers (such as dates)" and tick that box.
Edit: here's an image.
  [[IMG]http://ubuntuforums.org/attachment.php?attachmentid=224122&stc=1&thumb=1&d=1347602088[/IMG]  ]("http://ubuntuforums.org/attachment.php?attachmentid=224122&d=1347602088")
[URL="http://ubuntuforums.org/attachment.php?attachmentid=224122&d=1347602088"] LibreOffice 3.5.4.2
 Default – English (South Africa)
 When I came to Language Settings, I decide to change this opinion (mine is English South Africa) to English USA, Copy >Paste Special>Detect Special Numbers the figures come like this 09/02/16
 format to Jan 1, 2004  result Sep 2, 2016 and the first date on the table changing to 2 of September. I decide to copy direct and paste apply Format >Clear Direct Formatting, result is correct and it can be calculate correct, the pain on this is to change to Language Settings to USA, if there is no other way.
 Thank you very much.    :P
[/URL][  ]("http://ubuntuforums.org/attachment.php?attachmentid=224122&d=1347602088")

---

### Post by Vaphell on 2012-09-17
how does the original data look?

Date formats are inherently ambiguous in their short forms, most of the world uses y/m/d or d/m/y while USians use crappy m/d/y.

---

