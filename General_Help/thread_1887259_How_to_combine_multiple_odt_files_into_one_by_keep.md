---
title: "How to combine multiple odt files into one by keeping an old format of those files?"
date: 2011-11-26
forum: General Help
---

### Post by totalmachine on 2011-11-26
I tried to combine two odt files into the one with "Insert -> Insert File" function, but files didn't keep their old format before they were separated. I tried also with transforming each file in pdf and then with pdftk try to combine them but I lost table of content in my new output pdf file. So I wonder is there any alternative method to keep old formats of my old odt files when I combine them and similar question is there an option with pdftk to keep my Table Of Content in side pane (cause i can only see 'Pages') when I combine two or more pdf files?

Thank in advance for your help

---

### Post by totalmachine on 2011-11-26
I want to tell that this file (file A) who was inserted in other odt file (file B)its previous format was losted, and a format of a file B became dominant in new output file.

---

### Post by Paddy Landau on 2011-11-26
It's difficult, because the correct way to format is using styles; and, of course, the styles in the two files (if they have different templates) will conflict with each other.

I have never used a [Master Document]("http://wiki.services.openoffice.org/wiki/Documentation/OOoAuthors_User_Manual/Writer_Guide/Working_with_Master_Documents"), but it may solve your problem.

---

### Post by totalmachine on 2011-11-26
Yes I thought on that, so probably there is no way to do it with odt files. What about pdftk? Is there possible to obtain my Table Of Content in there (index)?

---

### Post by Paddy Landau on 2011-11-27
> **totalmachine said:**
> What about pdftk? Is there possible to obtain my Table Of Content in there (index)?
I have not used PDFTK, but looking at the specifications, I imagine not.

---

### Post by totalmachine on 2011-11-27
I found this:

[Merge PDFs with gswn32c.exe to obtain Bookmarks in new PDF file (look at the comments on the page)]("http://stackoverflow.com/questions/2969479/merge-pdfs-with-pdftk-with-bookmarks")

, but didn't try yet. I tried with Master Document but its quite difficult to do cause output in Master Document was quite messy when I imported files in it. Probably, if I would use Master Document at start (I'm writing my thesis) would be so much easier probably. The reason I split my thesis into two pieces is cause in first 5 pages of my thesis I don't need footers or headers and in other part I do. Now I will try with gswin32.exe (you need wine emulator to install it), maybe I will succeed in my aim to obtain Toc (Table OF Content) -> Bookmarks in pdf in my new output pdf file after the merge.

---

### Post by Paddy Landau on 2011-11-27
> **totalmachine said:**
> The reason I split my thesis into two pieces is cause in first 5 pages of my thesis I don't need footers or headers and in other part I do.
Learn to use styles effectively. It will save you many, many headaches. The correct way is to have one page style without the headers and footers, and another with. Set the first five pages to the one page style and the remainder to the other.

---

### Post by totalmachine on 2011-11-27
How can I do that in LibreOffice 3.4, cause when I choose to have footer and header that is applied on a whole document. I searched for that option before but didnt find it so cause of that I decide to split my thesis into two parts so that I can manipulate styles in each document indepenedtly.

---

### Post by Paddy Landau on 2011-11-28
> **totalmachine said:**
> How can I do that in LibreOffice 3.4, cause when I choose to have footer and header that is applied on a whole document. I searched for that option before but didnt find it so cause of that I decide to split my thesis into two parts so that I can manipulate styles in each document indepenedtly.
You need to learn all about styles. Google tutorials Open Office styles (Libre Office is a fork of Open Office); for example, in [Tutorials For Open Office]("http://www.tutorialsforopenoffice.org/category_index/wordprocessing.html"), Chapter 3 teaches you the basics of styles including (in Lesson 3) page styles. Also check out [Open Office's official Documentation Wiki]("http://wiki.services.openoffice.org/wiki/Documentation/Tutorials").

Briefly:

[LIST]
[*]By default, Libre Office uses a page style appropriately named *Default*.
[*]If you press F11, you will see the Styles and Formatting box. Click on the Page Styles tab, where you can create a new page style.
[*]On any page, you can change its current style: Right-click the word *Default* at the very bottom of the window in the status bar, and you can change that page's style.
[*]You can therefore set the *Default* page style to have headers and footers, and create a style named (say) *Front Pages* to have none.
[/LIST]
 
You may find it useful to learn about Sections after learning about Styles, because in certain situations they work together.

It's a bit of learning that you need to do, but it shouldn't take more than two or three hours. The time you save in future will be more than offset by the time you spend now on learning about them.

---

### Post by totalmachine on 2011-11-28
Thx

---

