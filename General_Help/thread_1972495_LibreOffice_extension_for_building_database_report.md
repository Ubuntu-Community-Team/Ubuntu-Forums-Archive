---
title: "LibreOffice extension for building database reports"
date: 2012-05-03
forum: General Help
---

### Post by DwalerXIII on 2012-05-03
I upgrqded to 12.04 and everything works well. Only for one thing: I cannot install the LibreOffice extension for building database reports. In the softwarecentre it is marked as installed but inn does not appear in the extension list of libreoffice.
I don't know if this has something to do with it but in the softwarecenter the package is called_ openoffice_.org-report-builder.

I searched the web and found a couple of alternative packages (Debian and ubuntu) but they had dependency problems.

I need this extension because the reports previously made in Base need the report builder.

---

### Post by DwalerXIII on 2012-05-05
Is someone capable of using the libreoffice report builder?

---

### Post by pezball on 2012-05-13
Seems like no one cares to reply this thread, I got same problem along with everybody else who uses LibreOffice Base in 12.04. The reason is that the report-builder package has been removed from the repository!!! See here: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/992232](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/992232)
 
Apparently too many dependencies or something like that... no idea what will happen... Base is pretty useless without reports I would say...
 
It might even be that the LibreOffice Base package has been compiled to not use the report builder at all, cos otherwise it would probably need it to be installed.  Means it will not work even if you manually install libreoffice-report-builder-bin

---

### Post by vasa1 on 2012-05-13
> **pezball said:**
> Seems like no one cares to reply this thread, ...
While that is possible, it is also likely that the thread was pushed off the "front page" and, unless one specifically searches for tags related to the topic, this thread may have become invisible to people who didn't spot it before it got pushed off the "front page".

Front page = 250 posts shown by clicking "New Posts".

This, I am afraid, is a feature of the forum because "New Posts" includes not just requests for help, which is the primary purpose of the forum if I understand correctly, but an assortment of posts unrelated to Ubuntu, the distro.

The other point why it appears that "no one cares" is that Base is not the most commonly used part of the Office suite. So the chances of a Base user coming along, IMO, aren't that hot.

Anyway, some other places to ask are:
[http://user.services.openoffice.org](http://user.services.openoffice.org) (they do answer questions about LibreOffice as well)
[http://ask.libreoffice.org/questions/](http://ask.libreoffice.org/questions/)
[http://nabble.documentfoundation.org/](http://nabble.documentfoundation.org/)

---

### Post by Yojji on 2012-06-01
I had the same problem.  The ask.openoffice forum has a post about this issue but there were no solutions.  I really needed to run reports so I had to install OpenOffice.

---

