---
title: "gedit taglist and document focus"
date: 2010-12-12
forum: General Help
---

### Post by L a r r y on 2010-12-12
Back in Ubuntu 6.06 I edited the xhtml.tags.gz XML file to give me a common list of xhtml tags that I use in my everyday web page editing.  It was at a time when an xhtml editor was not readily available off-the-shelf.

Gedit came packaged with xhtml.tags.gz and other language taglists, but its alphabetical listing by name of tags and attributes was not helpful to me, so I edited some new tag groups containing tags organized in a way more suitable to myself.

By breaking it down into tag groups that typically didn't require a lot of scrolling to find what I wanted, and by having head tags in one menu and body tags in another, it cut down on having to sort through the hundreds of tags to choose from.

I also created a menu for editing the taglist itself as well as one for when I was writing rich-text email that would be copied into a mailing list program form. 

**It worked flawlessly until a recent update brought with it a new version of gedit.**
It either was when I upgraded from 8.08 to 9.09 or from 9.09 to 10.04, I don't remember which.

**Example of how it works:**
An example:  I click on "body" on the left  pane and I would get at the current cursor position this insert:```
<body>
| (grey highlight indicates current line in document)
</body>
```The V-bar indicates the cursor position in the document.

I can either hit another tag to be inserted on the current line or begin typing text.

Since the upgrade, I can either hit another tag to be inserted at the current line, or **I have to select** the current line in order to type, even though it is already highlighted.

**EDITING THE TAG LIST**
To create a tag for the left side involves something like:```
<gedit:TagGroup name="03-XHTML Body Elements">
<gedit:Tag name="body">
<gedit:Begin>&lt;body&gt;
</gedit:Begin>|
<gedit:End>
&lt;/body&gt;
</gedit:End>
</gedit:Tag>
```
Shown here is a gedit "tag group" followed by a "body" tag.  The tag group creates a menu titled "03-XHTML Body Elements" and upon selecting that menu there is first thing listed a "body" tag.

The code from "<gedit:Tag name=" through </gedit:Tag>" is the complete set of instructions for a body tag set to be entered as shown above.

The code from "<gedit:Begin>" through "</gedit:Begin>" writes the opening "<body>."

The current line is also set in the document after the end of the "</gedit:Begin>" segment.  An entire tag that does not require any user input may be written in the "Begin" segment and there is no need for the "End" segment at all.  Such a tag will be entered into the document with the current line and cursor position following the tag.

The "<gedit:End>" writes the "</body>" code after the current line.


As I recall, when I first created my rendition of the xhtml.tags.gz file, a V-bar was used to indicate current position of the cursor, placed after "</gedit:Begin>."

However, as I go through this writing, it seems that just having a Begin and End should take care of that, for when I looked at the file I had no v-bars.  Adding them didn't change the behavior.


**Maybe related:**
I note that when I open a "Save as" dialog, I have a file name highlighted, and all but the extension is highlighted.  If I type, I replace the highlighted file name.

If instead, I first select a different location in the directory tree, and want to then choose a name, I still find the file name highlighted and attempt to type in a new name.  The silly highlight indicates that it is active, but it really isn't and the focus is in the directory tree instead.

Similarities:  The focus is in a different pane than where I expect the typing focus to be. 
 
*For gedit, the focus is in the left pane containing the tag list and not restored to the document's pane.
*For the Save-As window in just about any application, the focus is in the tree while an active highlight color is displayed on the file name.  (Possibly the Active and Inactive colors are the same on my system.)

And to click on the file name to bring it focus kills the advantage of having just the name portion selected, for a subsequent highlight will select the name and extension.

**Work-around for Save As dialog**
Instead of clicking with the mouse after selecting a location in the tree first, just use ALT-N to restore focus in the file name while retaining its name-only selection.


What solution might there be to restore focus to the document after using a tag list selection in gedit?

---

### Post by L a r r y on 2010-12-13
I have discovered that after inserting an HTML tag from the left pane into my document in the right pane, if I hit Tab three times I regain focus where the cursor is supposed to be in my document.

A process that used to involve typing, clicking on the left to insert a new paragraph tagset, then typing in the new paragraph, now involves:

Typing in the document, click on the left to insert a new paragraph tagset, hit Tab, Tab, Tab, and start typing the new paragraph.

Finish the paragraph, insert the next paragraph tags, Tab, Tab, Tab, and type the next paragraph.

If you hit four tabs, the fourth tab indents the cursor in the document.

It would be nice if it worked the way it used to in 8.08 and earlier, when typing focus was automatically set to the document after entering the new tag.

> **L a r r y said:**
> Back in Ubuntu 6.06 I edited the xhtml.tags.gz XML file to give me a common list of xhtml tags that I use in my everyday web page editing.  It was at a time when an xhtml editor was not readily available off-the-shelf.

Gedit came packaged with xhtml.tags.gz and other language taglists, but its alphabetical listing by name of tags and attributes was not helpful to me, so I edited some new tag groups containing tags organized in a way more suitable to myself.

By breaking it down into tag groups that typically didn't require a lot of scrolling to find what I wanted, and by having head tags in one menu and body tags in another, it cut down on having to sort through the hundreds of tags to choose from.

I also created a menu for editing the taglist itself as well as one for when I was writing rich-text email that would be copied into a mailing list program form. 

**It worked flawlessly until a recent update brought with it a new version of gedit.**
It either was when I upgraded from 8.08 to 9.09 or from 9.09 to 10.04, I don't remember which.

**Example of how it works:**
An example:  I click on "body" on the left  pane and I would get at the current cursor position this insert:```
<body>
| (grey highlight indicates current line in document)
</body>
```The V-bar indicates the cursor position in the document.

I can either hit another tag to be inserted on the current line or begin typing text.

Since the upgrade, I can either hit another tag to be inserted at the current line, or **I have to select** the current line in order to type, even though it is already highlighted.

**EDITING THE TAG LIST**
To create a tag for the left side involves something like:```
<gedit:TagGroup name="03-XHTML Body Elements">
<gedit:Tag name="body">
<gedit:Begin>&lt;body&gt;
</gedit:Begin>|
<gedit:End>
&lt;/body&gt;
</gedit:End>
</gedit:Tag>
```
Shown here is a gedit "tag group" followed by a "body" tag.  The tag group creates a menu titled "03-XHTML Body Elements" and upon selecting that menu there is first thing listed a "body" tag.

The code from "<gedit:Tag name=" through </gedit:Tag>" is the complete set of instructions for a body tag set to be entered as shown above.

The code from "<gedit:Begin>" through "</gedit:Begin>" writes the opening "<body>."

The current line is also set in the document after the end of the "</gedit:Begin>" segment.  An entire tag that does not require any user input may be written in the "Begin" segment and there is no need for the "End" segment at all.  Such a tag will be entered into the document with the current line and cursor position following the tag.

The "<gedit:End>" writes the "</body>" code after the current line.


As I recall, when I first created my rendition of the xhtml.tags.gz file, a V-bar was used to indicate current position of the cursor, placed after "</gedit:Begin>."

However, as I go through this writing, it seems that just having a Begin and End should take care of that, for when I looked at the file I had no v-bars.  Adding them didn't change the behavior.


**Maybe related:**
I note that when I open a "Save as" dialog, I have a file name highlighted, and all but the extension is highlighted.  If I type, I replace the highlighted file name.

If instead, I first select a different location in the directory tree, and want to then choose a name, I still find the file name highlighted and attempt to type in a new name.  The silly highlight indicates that it is active, but it really isn't and the focus is in the directory tree instead.

Similarities:  The focus is in a different pane than where I expect the typing focus to be. 
 
*For gedit, the focus is in the left pane containing the tag list and not restored to the document's pane.
*For the Save-As window in just about any application, the focus is in the tree while an active highlight color is displayed on the file name.  (Possibly the Active and Inactive colors are the same on my system.)

And to click on the file name to bring it focus kills the advantage of having just the name portion selected, for a subsequent highlight will select the name and extension.

**Work-around for Save As dialog**
Instead of clicking with the mouse after selecting a location in the tree first, just use ALT-N to restore focus in the file name while retaining its name-only selection.


What solution might there be to restore focus to the document after using a tag list selection in gedit?

---

### Post by L a r r y on 2010-12-31
I can add that I tried a centOS liveCD and had the same problem with gedit outlined here.  CentOS is a Red Hat RPM compatible Linux that has a gnome desktop, with a 7-year support cycle.

Because of the long-term support, they still run Firefox 3.0 and only support ext3 and Reiserts if I spelled that right.

I got my Windows XP running on another computer, and remembered what I don't like about Windows..... There was an update that insisted that I needed to restart my computer to finish the update, and it would pop up while I'm typing and stop my typing ding-ding-ding dead in its tracks.

In Windows, Firefox is not letting me keep my Google preferences cookie but in Linux it is not an issue.

Just a little update while we prepare to enter the new year.

Happy New Year!

Anyone have any ideas about how to resolve the gedit issue that is the topic of this thread?

Thanks!

[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif) <+++ Supposed to be a smiley!

---

