---
title: "OpenOffice.org Calc hyperlinks not working"
date: 2009-07-03
forum: General Help
---

### Post by Explosion85 on 2009-07-03
When I make a hyperlink in OpenOffice.org 3 Calc, nothing happens when I click on it. I even tried holding ctrl while clicking and still nothing. I want it to open Firefox just like any other normal link.

I have looked everywhere and I couldn't find an answer.

---

### Post by cmckdub on 2009-07-10
Explosion85:
I am also having a weird problem with hyperlinks in OpenOffice. Have you tried right clicking on the link to choose Open Hyperlink?

What version of OpenOffice are you using? What version of Ubuntu? This information seems to be significant.

When I use OpenOffice 3.0 to open a Microsoft Office docx document with a hyperlink in it, the document opens fine. Then if I  ctrl-click on the link, it attempts to open the link in OpenOffice :confused: momentarily, then closes OpenOffice. If I attempt to restart OpenOffice, it attempts to recover 2 documents, but fails. I need to cancel the recovery to successfully start OpenOffice.

I have tried saving the document as odt - no difference. 
I have tried copying that portion of the document into a new odt document - no difference - it still closes when trying to open the link. If I right click on the link and choose Open Hyperlink, it tries to open the hyperlink in OpenOffice and then closes.
I then create a diferent link in calc or type a new different hyperlink in OpenOffice Writer and ctrl-click on this different link it works fine - opens the hyperlink in Firefox as it should - new tab.
If I re-type the same hyperlink as originally caused the problem in text or link text in calc, as explosion85 has done, it opens the webpage in OpenOffice Writer and does not close.

I have looked at the following entries:
[http://ubuntuforums.org/showthread.php?t=562331](http://ubuntuforums.org/showthread.php?t=562331)
Seemed a bit old. But I went to:
[http://www.oooforum.org/forum/viewtopic.phtml?t=51992](http://www.oooforum.org/forum/viewtopic.phtml?t=51992)
and
[http://www.oooforum.org/forum/viewtopic.phtml?t=55923](http://www.oooforum.org/forum/viewtopic.phtml?t=55923)
but I keep finding myself looking for files that do not exist...

I am using Ubuntu hardy, with OpenOffice 3.0. Gnome.

There is no file in /usr/lib/openoffice/program called open-url.
There is nothing in /opt for OpenOffice.
the offending hyperlink is:
[http://science.uniserve.edu.au/school/quests/index.html](http://science.uniserve.edu.au/school/quests/index.html)

If this were a bug, I thought someone would have come across it before. So I assume Explosion85 and I each have some setting wrong somewhere...?

---

