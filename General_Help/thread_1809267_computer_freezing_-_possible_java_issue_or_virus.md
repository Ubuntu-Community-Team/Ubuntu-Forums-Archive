---
title: "computer freezing - possible java issue? or virus?"
date: 2011-07-21
forum: General Help
---

### Post by Camdent on 2011-07-21
My computer is giving me some very strange symptoms, so I'm not sure quite what to call this.  It generally starts when I'm watching something on Hulu, using Firefox (version 3.6.9, i think).  The computer freezes completely in one of the following ways: 

- screen just freezes
- screen freezes, with a 1-2 second audio repeat on whatever i was watching, like a record skipping
- screen turns into a bizarre pattern of short lines, sort of like a staircase pattern, usually in the color tones of my desktop.  

When it freezes, everything stops functioning and my only option is to do a hard shutdown (using the power button).  

Sometimes a show will play for 30 minutes to an hour with no problem, sometimes it freezes just a few minutes in.  But it happens constantly, every time I try to watch something. 

Here's where it gets interesting.  I tried to install another browser to see if it was an issue with firefox, but the Ubuntu Software Center also doesn't work. It can't load search results or any of the standard categories.  It just keeps thinking indefinitely. 

I don't know much about Ubuntu.  I'm still learning.  Any ideas?

---

### Post by dino99 on 2011-07-21
either a graphic driver issue (not activated, check it) or a missing gstreamer codec (look at logs to find errors, then open synaptic to add the missing codec)

---

### Post by Chayak on 2011-07-22
That sounds more like a graphics driver or hardware issue.

---

### Post by mikejonesey on 2011-07-22
u'll need to check your logs; at next high usage, check what eats the cpu;
```
ps -eo pcpu,command --sort pcpu | tail -5
```

---

### Post by deserthowler on 2011-07-22
Just to add to the confusion,:confused: I had a similar problem and traced it to a bad memory chip.

Earl

---

### Post by Diametric on 2011-07-22
Yeah, probably not a virus - deff check the graphic drivers first.

---

### Post by wildmanne39 on 2011-07-22
Hi, also here is a link on freezing issues.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

