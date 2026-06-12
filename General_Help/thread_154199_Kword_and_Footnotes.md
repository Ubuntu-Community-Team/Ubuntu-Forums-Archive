---
title: "Kword and Footnotes"
date: 2006-04-02
forum: General Help
---

### Post by Hygelac on 2006-04-02
Is anyone else having this problem?  The footnotes in .kwd files seem to be massively corrupt.  For example, if I copy text and paste it into a new file, the footnotes disappear and my footnote numbers are scattered in random places (Sometimes in between the spaces in a double-spaced paragraph; to highlight one of these can cause Kword to then crash!  This tends to happen if I close and reopen a 'corrupt' file.).  A random portion of a footnote might remain, often stuck in the margin of the top-left corner in a strangely-formatted box.  Sometimes when I try to add a footnote it is invisible, and may reappear (and disappear again) somewhere depending on how much I type.  I would be using OpenOffice, but it is really useless under 64bit.  ](*,)  As I said, is anyone else familiar with anything similar to this?  If so, **how can I stop it**?  I'm trying to write an essay and this is really making it difficult...

---

### Post by gingermark on 2006-04-02
I did a search for "kword footnote" at bugs.kde.org and whilst there are a few that sound similar to your problem, none of them seemed to be "it".

I don't know how to solve your problem. However, I have to ask which version of KOffice you are using?

KOffice 1.5 rc 1 is available for Breezy ([here](http://kubuntu.org/announcements/koffice-15rc1.php)) and maybe upgrading from an older version might help?

---

### Post by Hygelac on 2006-04-02
I was using the older 1.4.1.  I'll have to check-out that update.  The file I was working in is hopelessly mangled now and almost completely useless.  :(  At least I was able to piece everything back together by opening it several times (each time is different) and copy-pasting it into Kate (no nice formatting, but at least I can work in a stable environment).  I'll have a wee bit of work after that putting it back into Kword all in one shot so I can then export it as PDF.  This is not fun...

---

### Post by bailout on 2006-04-02
Try the 1.5 version. It uses the same open document format as open office so perhaps the footnote function will be more robust.

---

### Post by Hygelac on 2006-04-04
I guess I will try it then.  Why isn't it in the standard repositories right now though?

---

### Post by gingermark on 2006-04-04
[QUOTE=Hygelac]I guess I will try it then.  Why isn't it in the standard repositories right now though?[/QUOTE]
As I understand things, only security updates enter into the standard repositories. It's to do with stability. BUt you should see new versions of software in additional repositories, such as backports, as well as the ones that Kubuntu.org provide.

---

### Post by Hygelac on 2006-04-04
Neat, that section of Kubuntu.org announcements has a whole load of updates (now I have the new KOffice and a new KDE and amaroK :) ).  Is there a central repository of these things that I could add (i.e.: deb [http://kubuntu.org](http://kubuntu.org) breezy main)?
In about two weeks I will need to use footnotes again, so I will tell you how they work.  The default to .odt may change everything (hopefully).

---

### Post by gingermark on 2006-04-04
[QUOTE=Hygelac]Is there a central repository of these things that I could add (i.e.: deb [http://kubuntu.org](http://kubuntu.org) breezy main)?[/QUOTE]

Sort of. Check my sig for a decent list of official and unofficial repositories, but use the unofficial ones with care (esp. Serveas')

As far as the kubuntu.org ones go, these should be what you;re looking for:

deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) breezy main
deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) breezy main
deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) breezy main

Those three should give you the latest versions of most KDE software.

---

### Post by Hygelac on 2006-04-24
[QUOTE=Hygelac]In about two weeks I will need to use footnotes again, so I will tell you how they work.[/QUOTE]

I tried it yesterday and they still have the same problem. :( In the end I just did the footnotes manually; I'm anxious to see a more robust footnote feature in KWord.

---

