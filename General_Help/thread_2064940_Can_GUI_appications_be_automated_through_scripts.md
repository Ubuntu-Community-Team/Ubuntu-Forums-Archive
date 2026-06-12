---
title: "Can GUI appications be automated through scripts?"
date: 2012-09-30
forum: General Help
---

### Post by yoreei on 2012-09-30
Say we have a GUI applications that has an input field. Is it possible to access this input field with another application? The GUI application doesn't have a CLI version
I am asking in the Ubuntu forums and not in programming forums because I think it must be something OS specific. 

Thanks!

---

### Post by nigelenki on 2012-10-01
more Windowing System and Toolkit specific.

If you can pull up a window name from a window list; switch focus; shift field focus and stuff keys; then you can do this.  Problems may arise with, for example, knowing where focus is (i.e. in the wrong text box) before hand.  It'll probably be different between Metacity/KDE/sawmill and between GTK/QT.

---

### Post by NewAmercnClasic on 2012-11-13
Why specifically would this be of interest may I ask?

---

### Post by Jason80513 on 2012-12-08
The short answer is yes, because that's what automated testing software has to do.

The long answer is - you didn't explain what you wanted to accomplish (the what). Instead, you asked for the technical solution (the how). If you aren't using this to test your software, you are probably asking for a very bad, flakey, frustrating solution. The kind that keeps you busy fixing it, over and over again, for years to come. 

CLI or API will serve you better.

---

### Post by cariboo on 2012-12-09
Moved to General Help, as it has nothing to do with the threads it was in.

---

### Post by Habitual on 2012-12-09
[QUOTE=]...The GUI application doesn't have a CLI version
...[/QUOTE]

I'd be surprised if it didn't.
It may help us to know what program you are referring to...
It may be possible to **pass** *arguments* to the "GUI application"

Please let us know...

---

