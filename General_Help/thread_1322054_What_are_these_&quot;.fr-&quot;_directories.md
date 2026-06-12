---
title: "What are these &quot;.fr-*&quot; directories?"
date: 2009-11-10
forum: General Help
---

### Post by amanda on 2009-11-10
I have three hidden directories in my own home directory, each named something like ".fr-*"

drwx------  3 amanda amanda   4096 2009-09-23 12:09 .fr-AnmIr9
drwx------  3 amanda amanda   4096 2009-09-23 11:58 .fr-cIGcnw
drwx------  2 amanda amanda   4096 2009-09-16 12:52 .fr-SW9R2T

One appears to contain a complete replica of my home directory. What are these directories? What is creating them?

---

### Post by quixote on 2009-11-11
Very strange.  What's the most recent date on these dirs or their files?  If it's months ago, maybe it's just some garbage from a system crash?  If none have been updated recently, they may not be anything you need.

Alternatively, you could look at some of the files you did not create in a text editor, and see if there's header information telling you where they come from.

What I tend to do with weird junk I can't figure out is just delete it and hope for the best. :)  That's worked so far.

---

### Post by amanda on 2009-11-12
They're all from late September. 9/23 and 9/16. So weird. I did have some major crashing around then (my drive filled up--foiled by podcasts) but I'd really like to know where they came from!

-A

---

### Post by quixote on 2009-11-12
It may be hard to figure out.  If you're worried that they might be some kind of evidence of malware, I doubt very much it's a concern.  In that case discussions about strange .fr files would be all over the forums.

As I said, if you're curious, the thing I'd try would be to look at some of the weirder files with a text editor and see what you can see.

In general, life's too short to worry about the detritus of computers losing their tiny minds. :D  I'd just delete them and not worry about it.

---

### Post by winotree on 2009-11-12
A cursory check of Google seemed to indicate that Rapidshare uses the* fr* suffix on some of its downloads -- does this ring a bell??

---

### Post by amanda on 2009-12-11
Rapidshare? Nope.

And sadly, I came into possession of a new computer shortly before an upgrade borked the laptop where these puppies lived. So I might never know.

---

### Post by amanda on 2010-01-15
I just moments ago tried to open an html file that was in a still compressed ".zip" file. The URL? 

file:///home/amanda/.cache/.fr-O74gM6/...

So I'm guessing they're leftover from trying to make too big zip archives (like, say, a backup of my whole home directory, or most of my home directory). Something like that. 

Weird that Karmic seems to put them in ".cache" where Jaunty didn't.

---

