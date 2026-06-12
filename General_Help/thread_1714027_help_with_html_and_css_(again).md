---
title: "help with html and css (again)"
date: 2011-03-24
forum: General Help
---

### Post by Nick-S on 2011-03-24
Greetings everyone I need some help with my page again.
the problem: there is an empty unnecessary space at the bottom of the page. 
How can I get rid of it without messing up the main content?
My page is in pre-alpha stage so I am sorry if it looks ugly. 
I have attached my page for review.
your help would be greatly appreciated.

Nick

---

### Post by Nick-S on 2011-03-25
Anyone?

---

### Post by WorMzy on 2011-03-25
In short, it's because you're displaying content in block divs, then using a combination of relative and absolute placements to move them into position with CSS.

Use tables instead.

Also, I highly recommend that you read through [this entire website]("http://www.w3schools.com/html/default.asp").

---

### Post by Nick-S on 2011-03-25
> **WorMzy said:**
> In short, it's because you're displaying content in block divs, then using a combination of relative and absolute placements to move them into position with CSS.

Use tables instead.

Also, I highly recommend that you read through [this entire website]("http://www.w3schools.com/html/default.asp").

Is it possible to eliminate the space without using tables?

---

### Post by asmoore82 on 2011-03-25
> **WorMzy said:**
> In short, it's because you're displaying content in block divs, then using a combination of relative and absolute placements to move them into position with CSS.

Use tables instead.
This is horrible advice. Overuse of the <table> tag is the scourge of HTML.
Only use the <table> tag to create ... Duh! tables.

Your page has all kinds of other problems, though:
0. ReactOS is *not* Linux.
1. you jump back and forth with uppercase in filenames and tags.
2. autoclosing tags need some space before the />
3. anchor tags <a> shouldn't be autoclosed
4. list items <li> should always be within lists, ordered <ol> or un- <ul>
5. no page content should be within the <head> block.
6. tag names make really poor and confusing class names.
7. you might want to make indented "code" blocks - they have no effect
on rendering the document but make it easier to upkeep.

#7 applies 10x more to style sheets as well.

The void space at the bottom goes away if you clean up and
properly close all of the <div> tags.

---

### Post by Nick-S on 2011-03-26
> **asmoore82 said:**
> This is horrible advice. Overuse of the <table> tag is the scourge of HTML.
Only use the <table> tag to create ... Duh! tables.

Your page has all kinds of other problems, though:
0. ReactOS is *not* Linux.
1. you jump back and forth with uppercase in filenames and tags.
2. autoclosing tags need some space before the />
3. anchor tags <a> shouldn't be autoclosed
4. list items <li> should always be within lists, ordered <ol> or un- <ul>
5. no page content should be within the <head> block.
6. tag names make really poor and confusing class names.
7. you might want to make indented "code" blocks - they have no effect
on rendering the document but make it easier to upkeep.

#7 applies 10x more to style sheets as well.

The void space at the bottom goes away if you clean up and
properly close all of the <div> tags.


Thanks a lot Ill give this a try.

---

