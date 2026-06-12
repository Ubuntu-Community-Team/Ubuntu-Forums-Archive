---
title: "format txt files for terminal and OpenOffice"
date: 2009-08-12
forum: General Help
---

### Post by e24ohm on 2009-08-12
Folks:
I am trying to format a few of my documents in simple text format, and saved as .txt or related type to be able to open with “cat”,VIM, and nano; however, I am building these documents with OpenOffice and Text Editor.

Question: When I set items up is it better to use the space bar for spacing or the tab key?

+-----------------------------+
| 1.0 Section                 |
+-----------------------------+

Is it better to use the space bar or the tab key in this situation for the trailing “|” ? I noticed that I have ran into issues in the past with this.

Note: for example I used the space bar to build the table in OpenOffice, but when I imported into this field box, the trailing "|" was on the second line.

thank you

---

### Post by e24ohm on 2009-08-12
It appears totally different when i type the message, but you get the point.

---

### Post by mcduck on 2009-08-12
Spaces or tabs should both work, but it's a lot easier to count the spaces in tabs, and way too easy to have one space too little or too many somewhere.

But your real problem is that aligning things that way only works if you use a monospace font. In a terminal that's the default, but graphical applications will cause problems as they usually default to normal fonts..

---

### Post by nikhilk on 2009-08-12
> **e24ohm said:**
> Question: When I set items up is it better to use the space bar for spacing or the tab key?

+-----------------------------+
| 1.0 Section                 |
+-----------------------------+

Is it better to use the space bar or the tab key in this situation for the trailing &#8220;|&#8221; ? I noticed that I have ran into issues in the past with this.

Wow, hold it right there trying to start a holy war are we ;) See these links [link1]("http://www.jwz.org/doc/tabs-vs-spaces.html"), [link2]("http://www.iovene.com/tabs-vs-spaces-the-end-of-the-debate/")

Well, it doesn't really matter if you keep to one uniform convention throughout the document.
TAB can lead to some quirks depending on one's editor setting so I personally use spaces only in my text documents. But still even after careful formatting, variable size fonts can screw it up so use fixed width fonts.

---

### Post by e24ohm on 2009-08-12
> **nikhilk said:**
> Wow, hold it right there trying to start a holy war are we ;) See these links [link1]("http://www.jwz.org/doc/tabs-vs-spaces.html"), [link2]("http://www.iovene.com/tabs-vs-spaces-the-end-of-the-debate/")

Well, it doesn't really matter if you keep to one uniform convention throughout the document.
TAB can lead to some quirks depending on one's editor setting so I personally use spaces only in my text documents. But still even after careful formatting, variable size fonts can screw it up so use fixed width fonts.wow...that was a good article...thanks...this really helped...now I guess it is time to go back through my C apps and clean them up. 

yeah I am just starting to learn VIM, and wow..i'm blown away at the options.

cheers..

---

### Post by e24ohm on 2009-08-12
> **mcduck said:**
> Spaces or tabs should both work, but it's a lot easier to count the spaces in tabs, and way too easy to have one space too little or too many somewhere.

But your real problem is that aligning things that way only works if you use a monospace font. In a terminal that's the default, but graphical applications will cause problems as they usually default to normal fonts..i think i was using "Courier New" in Open Office, and the default in Text Editor.

thanks.

---

