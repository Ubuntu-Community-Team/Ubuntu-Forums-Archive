---
title: "Open Office problem"
date: 2011-03-29
forum: General Help
---

### Post by whvw on 2011-03-29
No matter what I do, Open Office insists on rendering time as 00:00:00, instead of 00:00. It will change what I type to what it wants. Turning off word complete does nothing. Once I found a way around this, but it was not a permanent fix. The help section gives you formating codes but no instructions on how to use them. Can someone help?
Why oh why can't Cross Over run Word Perfect?

---

### Post by vanadium on 2011-03-29
I was perfectly able to run Wordperfect 5.1 on Dosbox.

That aside, it would help if you tell about the context. Is this in a table?

---

### Post by walt.smith1960 on 2011-03-29
> **whvw said:**
> No matter what I do, Open Office insists on rendering time as 00:00:00, instead of 00:00. It will change what I type to what it wants. Turning off word complete does nothing. Once I found a way around this, but it was not a permanent fix. The help section gives you formating codes but no instructions on how to use them. Can someone help?
**Why oh why can't Cross Over run Word Perfect?**

What version of WordPerfect are you trying to run?
[http://www.codeweavers.com/compatibility/browse/name/?app_id=1736](http://www.codeweavers.com/compatibility/browse/name/?app_id=1736)

WordPerfect doesn't have a great history with Wine AFAIK but perhaps codeweavers has figured it out.

---

### Post by tredegar on 2011-03-29
> **whvw said:**
> 
**Re: Open Office problem**
No matter what I do, Open Office insists on rendering time as 00:00:00, instead of 00:00. It will change what I type to what it wants. 
OO wordprocessor, spreadsheet, presentation, or *what* please?

In OO wordprocessor: Insert - Fields - Time 
The time is inserted.
R-Click the time field.
Fields
Edit as required.
Note "Time Fixed" fixes the time at the time the field was created.
"Time" inserts the current time, which is updated the next time the document is opened / printed.

---

### Post by whvw on 2011-03-29
> **vanadium said:**
> I was perfectly able to run Wordperfect 5.1 on Dosbox.

That aside, it would help if you tell about the context. Is this in a table?
Yes, it was in a table. I type "7:00" (or 07:00) and it types "07:00:00".

---

### Post by whvw on 2011-03-29
> **walt.smith1960 said:**
> What version of WordPerfect are you trying to run?
[http://www.codeweavers.com/compatibility/browse/name/?app_id=1736](http://www.codeweavers.com/compatibility/browse/name/?app_id=1736)

WordPerfect doesn't have a great history with Wine AFAIK but perhaps codeweavers has figured it out.
It is version 9. It will install, and I can actually get to the splash screen (you don't know how good I felt when I first saw that) but then an error message pops up and says "word perfect was not installed properly" Rats! I keep wondering it there is some file that isn't where WP thinks it is, and if I could copy it there manually, or perhaps lift the whole directory structure over from an old Winderz installation to the Cross Over (Wine) bottle?
I also heard that V12 would work under Cross Over, so I downloaded it but no dice.
Beyond that, I even have a disc of WP for Linux v.8, (even though I hear that 8.1 is the one I really need) but that would never install _[COLOR=Black]at all[/COLOR]_.
I've tried many word processors, but WP is by far the best.

---

### Post by walt.smith1960 on 2011-03-30
When you first log onto codeweavers.com and fill in the compatibility box, several versions of WordPerfect pop up.  9 is bronze, 11 & 12 are silver, X3 is gold. I haven't tried to install WP under wine or crossover but i've spent some time on WP's support forums watching threads about it.  I recall that installing everybody's favorite browser I.E. before trying WP is critical. I don't recall if .net framework is required or not.  I also remember something about disabling enhanced dialogs or WP under Wine will crash & burn.  I also seem to recall that installing in a Win98 bottle works best. I think X3 is the last version of WP that would run under Win9X.  

I've been using OO/LO because OO has a reputation for better MSO file compatibility and my office suite needs are pretty modest. After much development of MS Word and virtually no development of WP (I'm sure you know the tawdry history of Microsoft's involvement with Corel & WP) WP is *still* regarded as better for long document creation and management.  It doesn't support unicode though which is a deal killer for many.

---

### Post by vanadium on 2011-03-30
> **whvw said:**
> Yes, it was in a table. I type "7:00" (or 07:00) and it types "07:00:00".
I cannot reproduce that (but that could be my locale settings). However, turn of "number recognition" to avoid automatic changing of the input of numbers (right-click in table). To turn it of by default, change the option in Tools - Options.

---

### Post by whvw on 2011-03-30
Thanks. That seems to have done it. Hopefully, it will stay that way.

---

### Post by whvw on 2011-03-30
The problem was the need to turn off "number recognition", somewhat buried in "options"

---

