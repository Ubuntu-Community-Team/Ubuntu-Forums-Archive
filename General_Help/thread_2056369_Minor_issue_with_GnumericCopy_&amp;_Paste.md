---
title: "Minor issue with Gnumeric/Copy &amp; Paste"
date: 2012-09-11
forum: General Help
---

### Post by jzemeocala on 2012-09-11
Hello everyone, 

One of my jobs involves copying and pasting a lot of stuff into spreadsheets.
and for a variety of reasons that all boil down to speed and simplicity, I like to use gnumeric

For the most part, I have a quick copy and paste method that involves:
triple clicking a line of text
pressing ctrl+c
pressing alt+tab (back into gnumeric)
pressing tab to the next line
pressing ctrl+v
Pressing alt+tab (back to webpage)
repeat


This all works wonderfully and I get my work done rather quickly but I have one issue that tends to slow me down.

Sometimes I end up copying a space at the beginning of the line and I later have to go back and manually delete this space from all the lines that this happens in (which is several hundred most of the time)

I have tried several methods to circumvent this but all of them slow down my progress significantly. So I was wondering if there is any way that I can make either the clipboard or gnumeric itself ignore these spaces at the beginning of a copy or paste. 

I know that this seems like a trivial issue but it literally adds at least an hour to my work day. 


Any help or hints are greatly appreciated. 
Thanks in advance

---

### Post by kimberlite on 2012-09-11
When you have copied all you wanted search/replace in Gnumeric for
```
^\s*
```
This is a so called regular expression that means "space at beginning of the line". Replace it to nothing.

---

### Post by jzemeocala on 2012-09-11
Thanks for your reply.

But I just did that (putting the code in the search for box and leaving the replace box empty) and it didn't change anything.

I'm sorry but am I missing something

---

### Post by jzemeocala on 2012-09-11
Nevermind, I found that i had to set it to search for regular expressions instead of plain text.


Thank you so much. You have literally saved me hours of work

---

### Post by vasa1 on 2012-09-11
> **jzemeocala said:**
> Thanks for your reply.

But I just did that (putting the code in the search for box and leaving the replace box empty) and it didn't change anything.

I'm sorry but am I missing something

Did you enable regular expressions in the search and replace thingie? Perhaps under more options? (I don't use Gnumeric but I have to do that if my search term is a regular expression in LibreOffice Calc.)
If that's not done, the program will look for ^\s literally.

I'm not sure about ^\s* because even ^\s should work.

---

### Post by Elfy on 2012-09-11
Better that you remove the link yourself than I do it ;)

IF the issue is fixed - please mark your thread as solved :)

Thanks

---

### Post by jzemeocala on 2012-09-11
Done. Sorry about that.


But thanks again

---

