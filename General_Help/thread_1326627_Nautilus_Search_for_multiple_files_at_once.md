---
title: "Nautilus: Search for multiple files at once"
date: 2009-11-14
forum: General Help
---

### Post by sumpm1 on 2009-11-14
Here is my dilemma: Say I have a folder full of mp3 files. I want to find Metallica, Styx, Green Day, and Aerosmith songs. So as far as I can tell right now, I would have to do 4 different searches. I know of no way to for example enter in the search filed: "Metallica, Styx, Green Day, Aerosmith" and have Nautilus return files containing ANY of these terms. I really need to search for 50 or more terms, not just 4.

Is there any way to do this in Nautilus? If not, is there any program or script that would allow me to do a search like this in an interface?

Thanks

---

### Post by hwttdz on 2009-11-14
Ahh, you may have reached the point where the command line is more flexible and powerful than the graphical interface.  A few command line options are "ls *term1*.mp3 *term2*.mp3 ...", I'm personally fond of "ls|grep -E "term1|term2|term3"|xargs command".  Perhaps the first should be "command *term1*.mp3 *term2*.mp3 *term3*.mp3".

Of course you could make a script, but unless you're doing something rather complicated it seems unnecessary.

---

