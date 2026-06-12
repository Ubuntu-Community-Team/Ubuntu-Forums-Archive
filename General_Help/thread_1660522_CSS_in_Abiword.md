---
title: "CSS in Abiword"
date: 2011-01-05
forum: General Help
---

### Post by MichaelBurns on 2011-01-05
As much as it pains me, I'm finally coming to accept that **LaTeX** is not the best tool to use for every kind of document.  More precisely, some people demand that I provide my resume to them as an **MS Word** file! (disgusting!)  So, I am trying out **Abiword**.  Of course, coming from **LaTeX**, I suspect that any word processor will be incredibly frustrating.  I want to set up my **Abiword** experience to separate, as much as feasible, the content from the presentation.

In **LaTeX**, I have a style file where I define various commands and environments.  I wish that I could do the same thing in **Abiword**.  Why anyone demands **.doc** over **.pdf** I cannot understand (Is **.pdf** somehow not supported in **MS Windows**?), unless their intention is to modify the document without my consent or steal the template that I spent all day to create.  (jerks!)

My idea is to use a **CSS** (*something* style sheet, I think).  I am quite unfamiliar with **CSS** even in **html**, but, from what I've read, I think that a **CSS** is the way to go.  Can someone help me to get started with this in **Abiword**.  (I cannot find the help that I need from the Abiword "documentation", neither off- nor on-line.)  Or, does anyone have a better suggestion?  Also, when I export to **.doc** (jerks!), will it automatically generate the correct presentation in the **.doc** itself, or do I need to send the style file along with the **.doc** file (annoying)?

---

### Post by MichaelBurns on 2011-01-06
It hasn't been 24 hours yet, but I made a little bit of "progress" that I thought I could share.  Apparently, AbiWord essentially just creates **xml** files, and stores style information in a monstrous <style> element (in the "header"?).  I have been spending so many hours trying to make sense of it all.  Of course, I'm sure that Abi would prefer me to use her front end (:D), but it is just so frustrating not to know why a table cell suddenly shoots off to the right, or why I can't remove all of that whitespace.  (and I hate using the mouse)

---

### Post by ubunt2guy on 2011-01-06
> **MichaelBurns said:**
> As much as it pains me, I'm finally coming to accept that **LaTeX** is not the best tool to use for every kind of document.  More precisely, some people demand that I provide my resume to them as an **MS Word** file! (disgusting!)  So, I am trying out **Abiword**.  Of course, coming from **LaTeX**, I suspect that any word processor will be incredibly frustrating.  I want to set up my **Abiword** experience to separate, as much as feasible, the content from the presentation.

In **LaTeX**, I have a style file where I define various commands and environments.  I wish that I could do the same thing in **Abiword**.  Why anyone demands **.doc** over **.pdf** I cannot understand (Is **.pdf** somehow not supported in **MS Windows**?), unless their intention is to modify the document without my consent or steal the template that I spent all day to create.  (jerks!)

My idea is to use a **CSS** (*something* style sheet, I think).  I am quite unfamiliar with **CSS** even in **html**, but, from what I've read, I think that a **CSS** is the way to go.  Can someone help me to get started with this in **Abiword**.  (I cannot find the help that I need from the Abiword "documentation", neither off- nor on-line.)  Or, does anyone have a better suggestion?  Also, when I export to **.doc** (jerks!), will it automatically generate the correct presentation in the **.doc** itself, or do I need to send the style file along with the **.doc** file (annoying)?

CSS = Cascading Style Sheets and is used to separate the style of a web page from the content.

Why don't you just try using Open Office?

---

### Post by MichaelBurns on 2011-01-06
> **ubunt2guy said:**
> Why don't you just try using Open Office?I did; I hate it.  No offense intended; just personal preference, but I can say that, for example, it takes literally over three minutes to load up on my machine, and then rudely just suddenly takes over when I'm trying to work in another window.

I should have been more clear:
> 
Can someone help me to get started with this in Abiword. ... Or, does anyone have a better suggestion?

I was inviting suggestions that provide an alternative to CSS, not AbiWord.  I don't want to discuss OpenOffice.org.  I think that I know how to use it, but I want a solution that I will be happier with in the long term.  I just find OpenOffice.org too bloated and sluggish for my purposes.  I do thank you for the reply.

Any AbiWorders out there?

---

### Post by Vaphell on 2011-01-06
not that it changes anything, but reportedly OO starts slow because of the java environment that is used by OO. You can disable it in OO options.

---

### Post by MichaelBurns on 2011-01-06
> **Vaphell said:**
> ... reportedly OO starts slow because of the java environment that is used by OO. You can disable it in OO options.Interesting, and perhaps even useful for future reference, however ...
> **MichaelBurns said:**
> I don't want to discuss OpenOffice.org.I wonder how I can clarify this further?

Does anyone here actually use AbiWord?

---

### Post by gluxon on 2011-01-06
Perhaps you can try using a converter? LaTeX allows you to export the file as a PDF, have you tried tools that then convert PDF to DOC?

LibeOffice can do this by simply opening up the PDF, and saving as a DOC. (Technically, we didn't discuss OpenOffice further).

You could even try converting LaTex file to and RTF, and then DOC :)

[http://en.wikibooks.org/wiki/LaTeX/Export_To_Other_Formats#Convert_to_RTF](http://en.wikibooks.org/wiki/LaTeX/Export_To_Other_Formats#Convert_to_RTF)

---

### Post by Yellow Pasque on 2011-01-06
Send the resume in .pdf format anyway. Even the most clueless user with Win XP SP1 and IE6 will probably have acrobat reader somewhere on his/her machine. You could also use latex2rtf to convert your resume to rtf and see if it looks "close enough."

> Does anyone here actually use AbiWord?
I do, but my word processing needs are really basic.

---

### Post by MichaelBurns on 2011-01-07
Thank y'all for the latex suggestions.  Again, I may look into it for future reference, but I can't imagine that I would have much use for it.  I've gotta fire up a word processor in order to confirm the acceptability of the document presentation anyway ...
> 
Send the resume in .pdf format anyway.

What do you think, I just didn't send anything?  I'm telling you, these people *insist*!  My advice: don't be unemployed.

Getting back to abiword:
I think that I've almost figured it out.  After fumbling around in the xml, I realized that the "don't edit this file by hand" warning in the comment block is probably good advice.  It is just so tempting.  Anyway, I still need to tie off a few loose ends, but I have basically figured out how to implement styling as I initially intended.  (It just doesn't seem to provide as much control over things as, say, latex.)

Some lighthearted gripes (and hopefully someone can straighten at least one of these issues out for me):

Where's the documentation that explains the props attribute values (or anything else for that matter)?

The table tools are too basic.

The header section actually occurs at *the end* of the xml!

Can I do something like aliasing (e.g. #define or \newcommand) for element tags so that I don't have to type all of those damn attributes every time? (The xml was not very well thought out, IMO.  Listen to me, actin' all expert and stuff.)

What is the purpose of all of those xid attributes?  Can I just get rid of them?

The basedon attribute seems to be ignored (in the header section).

Why do the exported .doc, .rtf, and .html all look like total crap?  (Is my style just hopelessly unexportable?)

---

