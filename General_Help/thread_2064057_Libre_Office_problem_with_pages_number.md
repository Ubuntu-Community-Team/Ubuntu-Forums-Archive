---
title: "Libre Office problem with pages number"
date: 2012-09-28
forum: General Help
---

### Post by BSG Fan on 2012-09-28
I had a very large document consisting in about 700 pages, for my thesis.

I need to edit the document but LibreOffice (LibreOffice 3.4.4) began (several times) to crash. Sometimes it crashes in just 10 seconds, so I needed to start again the application, but the crashes continued happening. and when crashes, nothing not-saved is not saved.

So, I experimented by splitting the document in two parts (part A and part B) and seems is now working for good. No matter that part B still crashed one time (till now), I decided to continue with the 2 parts, instead of 3.


My question is:
if Part A is from page 1 to page 300,(automatically),
how I do to re-start Part B from page 301 and ahead?

I am trying to find that feature (I have seen before somewhere) but I can not find it.

Any clue?

Thanks in advance!

---

### Post by kurt18947 on 2012-09-28
I can't help with that but there have been some cases of people losing theses using Libre Office on machines with ext4 partitions.  They were not able to recover their documents.  If you haven't done so already, I'd strongly recommend backing up to a removable drive, and maybe saving as an rtf/doc/other non-odt format.  I hope that bug has been fixed but backups are cheap & easy.  Recreating all or most of a 700 page document is not.

---

### Post by Peter Maunder on 2012-09-28
You will find a place to change page numbers on the Insert Page break dialogue..

1 Add a "blank" page at the start of the next part of your document. 
2 Then Insert > Manual Break
3 Select Page break and choose style
4 Select Change Page Number and enter the number you want.

If you are using left and right hand pages, don't forget odd page numbers go on the right-hand page and even page numbers go on the left-hand page.

(Taken from the LibreOffice Writer guide)   Peter

---

### Post by LewisTM on 2012-09-28
From LibreOffice Help
[http://help.libreoffice.org/Writer/Page_Numbers#To_Start_With_a_Defined_Page_Number](http://help.libreoffice.org/Writer/Page_Numbers#To_Start_With_a_Defined_Page_Number)

> To Start With a Defined Page Number

Now you want some more control on page numbers. You are writing a text document that should start with page number 12.
Click into the first paragraph of your document.
Choose Format - Paragraph - Text flow.
In the Breaks area, enable Insert. Enable With Page Style just to be able to set the new Page number. Click OK.
The new page number is an attribute of the first paragraph of the page.
Cheers!

---

### Post by Peter Maunder on 2012-09-28
Have you thought of using a Master document and dividing your thesis into sections? The master document would then manage the formatting table of contents, index page numbers etc. otherwise if you add or delete pages in one section this would need to be reflect manually in the other sections.

If your thesis contains a number of images, you may need to adjust the memory cache settings.  ( Options > Memory) to improve performance and reduce memory thrashing.

Good luck with the thesis. It is great feeling once it is done.   Peter

---

### Post by BSG Fan on 2012-10-04
> **Peter Maunder said:**
> Have you thought of using a Master document and dividing your thesis into sections? The master document would then manage the formatting table of contents, index page numbers etc. otherwise if you add or delete pages in one section this would need to be reflect manually in the other sections.

If your thesis contains a number of images, you may need to adjust the memory cache settings.  ( Options > Memory) to improve performance and reduce memory thrashing.

Good luck with the thesis. It is great feeling once it is done.   Peter

Thank you a lot with the help.
I never have been used a Master document. I will check it how use it. It sounds a good idea.

Thank you :)

---

### Post by BSG Fan on 2012-10-04
> **LewisTM said:**
> From LibreOffice Help
[http://help.libreoffice.org/Writer/Page_Numbers#To_Start_With_a_Defined_Page_Number](http://help.libreoffice.org/Writer/Page_Numbers#To_Start_With_a_Defined_Page_Number)


Cheers!

Thank you LewisTM.
I appreciate it.

---

### Post by BSG Fan on 2012-10-04
> **kurt18947 said:**
> I can't help with that but there have been some cases of people losing theses using Libre Office on machines with ext4 partitions.  They were not able to recover their documents.  If you haven't done so already, I'd strongly recommend backing up to a removable drive, and maybe saving as an rtf/doc/other non-odt format.  I hope that bug has been fixed but backups are cheap & easy.  Recreating all or most of a 700 page document is not.

You are right! I always do a copy (version 1, version 2, etc) of the same document and I save a copy in my flash drive too just in case...
Experience....

Thank you.

---

### Post by BSG Fan on 2012-10-04
I have a question about how starting with certain page number in another document,,, let's say,, page 231.

the thing is that for that certain document, the page number is in the header only.

example: Lewis / The Last River / 231  
, instead of Lewis / The Last River / 1

where the 231 is to the extreme right in the header (top of page).

How can I manipulate the header, so I can start with page 231 there?

Thank you.

ps: I am using this page for that, but it fails in tell me what I want exactly:

[http://help.libreoffice.org/Writer/Inserting_a_Chapter_Name_and_Number_in_a_Header_or_a_Footer](http://help.libreoffice.org/Writer/Inserting_a_Chapter_Name_and_Number_in_a_Header_or_a_Footer)

---

