---
title: "How does Rhythmbox retrieve CD information (upon insertion) and how can I contribute?"
date: 2009-08-16
forum: General Help
---

### Post by newagelink on 2009-08-16
I'm using: [LIST]
[*]Ubuntu 9.04 - the *Jaunty Jackalope*
[*]Rhythmbox 0.12.0
[/LIST]

I inserted [The Croatian Prodigy]("http://www.anavidovic.com/html/purchase.html") by [Ana Vidovic]("http://www.anavidovic.com/"), and it came up as 'unknown CD', *etc*. After some digging, I also found that the Rhythmbox Help information appears outdated: It refers to Rhythmbox using Sound-Juicer, which isn't installed, and links to its manual, which returns an error when clicking. (The link to the Sound Juicer help info. works properly after installing Sound-Juicer and its dependencies from Synaptic Package Manager.)

So, I can apparently submit the CD information to MusicBrainz (used by Sound Juicer) and extract the CD via Sound Juicer, but why was Sound Juicer not included with the default installation? Should I not be using Sound Juicer with Ubuntu 9.04?

And what does Rhythmbox use to retrieve CD information, and how can I add the album information once for all so that next time I (or anyone else) inserts the CD, the correct track info. *etc.* will show up?

---

### Post by geirha on 2009-08-16
It gets it from freedb. [http://www.freedb.org/en/faq.3.html#21](http://www.freedb.org/en/faq.3.html#21)

---

### Post by newagelink on 2009-08-17
Thanks. Why does it use freedb instead of MusicBrainz?

---

### Post by newagelink on 2009-08-17
I installed Grip as the FAQ suggested. When attempting to submit track information to freedb, a notice popped up saying something like, 'You are about to submit information via email', possibly with a 'Yes' or 'No', or maybe it only said 'OK'.

After clicking 'Yes' or 'OK' (I forget which), the notice disappeared, and I received no notification of success or failure; no email composition popped up, and I opened Evolution (which I don't think I've correctly configured; I think it's better to use gmail, accessible everywhere than Evolution only accessible on my laptop) and there was no visible action ... So did it send? or not?

Grip is too complicated to rip CDs; the default settings rip in .wav format to some folder, and the Help documentation is too technical (and possibly incomplete) for me to edit the settings. :(

So ... is there a better way to contribute to Rhythmbox's CD identification? Did my attempt to submit tracks go through successfully? (If they did, then there is some delay because Rhythmbox still didn't recognize the CD.) What should I do?

---

