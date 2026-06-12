---
title: "Line-problem with LibreOffice Writer"
date: 2011-09-04
forum: General Help
---

### Post by merely on 2011-09-04
Greetings!

I hope I am posting this in the right place. These forums have been of great help to me with the two or so problems I've encountered with ubuntu so far. Both of which had to do with spontaneous deletions of core files. This is the first time I have been confused over one of Ubuntu's programs, specifically LibreOffice Writer.

I wanted to strip it down to a minimalist appearance, and played with the settings. The ruler went, and the toolbars. Just a word processor. A strange thing has happened, however - when I run the cursor down the lines of text, it halts, inexplicably, at certain lines. I notice that the next line is usually slightly odd - the lower loops on the 'g's cut off, and so forth. When I press the space bar, the problem is resolved for those two lines - the text shuffles and rearranges itself.

As I am working with a long document, this will make editing rather laborious, however. I have tried everything I can think of with the settings, and cannot seem to restore it to its former unproblematically flowing state. Can anyone offer a suggestion, or explanation about what's happened?

Thank you in advance.

---

### Post by Lampi on 2011-09-04
If I understand you correctly this is an old/annoying line rendering bug: it has been in Openoffice for years and they might have "ported" it to libreoffice, since nobody tracked it down in OO.

You might get rid of it using the proprietary graphic driver instead of the Xorg driver. I can't be sure this is still true, sine I no longer use fglrx.

I prefer using the Xorg driver, so I decided to add a shortcut key to refresh all content (menu extras > refresh > refresh all) It still can be pretty annoying with some large files, because most of the time the rendering will break again soon, causing you to hit refresh repeatedly. It is next to impossible to track down what file content triggers it - that could be the reason why it never got solved so far. It is rendering related, if you find a reason, post it here, I'll gladly test it. :)

---

