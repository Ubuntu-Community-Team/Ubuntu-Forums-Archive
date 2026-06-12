---
title: "LibreOffice bugs in window with ubuntu 12.04"
date: 2012-05-11
forum: General Help
---

### Post by David McCoy on 2012-05-11
Hi Everyone, 

I just upgraded to ubuntu 12.04 and now in Libreoffice, well, all the suits, the tab window with FILE, TOOLS, FORMAT etc. are all just dash lines, like this -, as well as if I right click in a page, my options show dashes only, no words come up.  I have the latest Libre version, and I used synaptic to uninstall and reinstall but no luck.  Does anyone have any solutions?

---

### Post by wilee-nilee on 2012-05-11
Go to home hit crtl-h find .configs and delete the libreoffice folder. A new one will be generated. If you have added any extensions they will be gone, as well as any dictionaries, but you can get all those of the libreoffice site. I have had what seems to be a similar problem.

---

### Post by David McCoy on 2012-05-11
Hi,

Thanks for the help. I opened Home, hit control H to show hidden folders and deleted the LibreOffice folder.  Reopened office and..still the same problem. That and in the Home folder I didn't see a new hidden file generated.  Any other suggestions! This is a pain since, of course, libre office is the only word editing program available! Thanks again for the reply!

---

### Post by wilee-nilee on 2012-05-11
> **David McCoy said:**
> Hi,

Thanks for the help. I opened Home, hit control H to show hidden folders and deleted the LibreOffice folder.  Reopened office and..still the same problem. That and in the Home folder I didn't see a new hidden file generated.  Any other suggestions! This is a pain since, of course, libre office is the only word editing program available! Thanks again for the reply!

Was it in the .config folder?

---

### Post by thatguruguy on 2012-05-11
The following will install a "global menu" (that is, the menu that shows in the top of the screen, like other programs in Ubuntu). It may not fix the problem, but it's worth a shot:
```
sudo apt-get install lo-menubar
```
I find it strange that a new .libreoffice directory wasn't generated when you opened LibreOffice again.

As far as other word processors, you can always install Abiword, Calligra, or Zoho. They're all available in the Ubuntu Software Center.

---

### Post by wilee-nilee on 2012-05-11
> **thatguruguy said:**
> The following will install a "global menu" (that is, the menu that shows in the top of the screen, like other programs in Ubuntu). It may not fix the problem, but it's worth a shot:
```
sudo apt-get install lo-menubar
```I find it strange that a new .libreoffice directory wasn't generated when you opened LibreOffice again.

As far as other word processors, you can always install Abiword, Calligra, or Zoho. They're all available in the Ubuntu Software Center.

They deleted the wrong folder I believe.

---

### Post by thatguruguy on 2012-05-11
> **wilee-nilee said:**
> They deleted the wrong folder I believe.

That's distinctly possible.  If he deleted the entire .libreoffice folder, it should have regenerated.

---

### Post by Jack Kelly on 2012-05-13
Hi,

I have the exact same problem as the original poster.

In an attempt to fix the problem, I closed LibreOffice, deleted [FONT="Courier New"]~/.config/libreoffice[/FONT] and re-started LibreOffice.  It automatically and silently created a new [FONT="Courier New"]~/.config/libreoffice[/FONT] directory but the original problem has not been resolved: I still cannot access the first few menus in Libre Office and, indeed, Libre Office seems rather unstable.  Whilst using Libre Office, I received a "Sorry, Ubuntu 12.04 has experienced an internal error" message (I sent an error report).

---

### Post by Jack Kelly on 2012-05-13
I just tried completely removing LibreOffice and reinstalling it.  This has not fixed the problem.

---

### Post by Jack Kelly on 2012-05-13
Installing [FONT="Courier New"]lo-menubar[/FONT] doesn't fix the problem, either (so I've uninstalled it).

---

### Post by Jack Kelly on 2012-05-13
Aha... this might be a multi-monitor problem.  If I disable my second monitor then the menus in LibreOffice works fine.  So I believe the bug I'm experiencing is the same as this one:

[Libreoffice on multiple monitors. Menus open in wrong monitor]("http://askubuntu.com/questions/135953/libreoffice-on-multiple-monitors-menus-open-in-wrong-monitor")

---

### Post by David McCoy on 2012-05-13
Yes, I tried all the recommended methods and still the menu does not work correctly.  I am at a complete loss at this point.  I did delete the correct file but still nothing has changed.

---

### Post by David McCoy on 2012-05-13
Yes, I tried all  the recommended methods and still the menu does not work correctly.  I  am at a complete loss at this point.  I did delete the correct file but  still nothing has changed.

---

### Post by Jack Kelly on 2012-05-14
@David - are you using a multi-monitor setup?  If so, the issue you're experiencing may to be related to the following reported but currently unresolved bug: [LibreOffice Bug 48168 - Menus positioned incorrectly on multi-monitor displays]("https://bugs.freedesktop.org/show_bug.cgi?id=48168").  If your situation does match the situation described in that bug report then I'd advise adding a comment to the bug report to show the developers that multiple people are experiencing this problem.

---

### Post by David McCoy on 2012-05-14
No I am not.  I am actually using a netbook.  Perhaps this is a result of resolution settings or the smaller screen? Has anyone else experienced this problem?

---

### Post by Jack Kelly on 2012-05-15
Interesting.  The issue you're experiencing does sound very similar to the issue I'm experiencing, even though you're not using dual monitors.  I'd still recommend posting a comment on the  [LibreOffice Bug 48168 - Menus positioned incorrectly on multi-monitor displays]("https://bugs.freedesktop.org/show_bug.cgi?id=48168") bug report describing your situation.  Describing the full range of situations in which this bug appears may help the developers fix the problem as quickly as possible (on the other hand, the bug you're experiencing may not be related... but I think it's worth mentioning your situation on the bug report).  The more activity the bug report receives, the more likely it is to be fixed quickly.

Thanks,
Jack

---

### Post by Jack Kelly on 2012-05-15
@David: can you see the menus if you reduce the size of the LibreOffice window before trying to access the menus?  (i.e. un-maximise the Calc/Writer window)

---

### Post by Jack Kelly on 2012-05-15
@David also, please could you show as a screenshot of the problem (for example a screenshot of what happens when you try to open the File menu.  Just hit the "print screen" (prt sc) button on your keyboard to save a screenshot)

---

### Post by David McCoy on 2012-05-17
@Jack, 

First thanks for all the assistance.  Yes, problem still persists.  It is not resolved when I minimize the window or shrink it, then maximize again.  Here are some snapshots of the problem.

---

### Post by Jack Kelly on 2012-05-17
@David

Thanks for the screen shots.  OK.  The problem you're experiencing is different the problem I'm experiencing.

However, I definitely remember seeing a bug described in the LO bugzilla that sounds very similar to yours.  I tried searching for the bug but I couldn't find it.  If you fancy it, you could try to locate the bug listed over on bugzilla.

To get started:

[LIST=1]
[*]Go to [https://bugs.freedesktop.org/query.cgi](https://bugs.freedesktop.org/query.cgi)
[*]Select Product = "LibreOffice", Status="All" and search for words like "menu"
[/LIST]

Good luck!

---

### Post by Jack Kelly on 2012-05-17
OK, this bug looks similar to yours: [https://bugs.freedesktop.org/show_bug.cgi?id=48202](https://bugs.freedesktop.org/show_bug.cgi?id=48202)  
 but I'm pretty sure I remember seeing another bug report similar to yours which had some more discussion of the problem.

---

### Post by David McCoy on 2012-05-21
@Jack, 

Thanks for the post, unfortunately it doesn't look like anyone has responded yet with solutions.  Looks like I'm just straight up stuck!

---

### Post by Jack Kelly on 2012-05-21
Try uninstalling "libreoffice-gtk".  That fixed the problem I was having with menus.  So even though we have different issues, this hack may fix both our issues.

---

### Post by David McCoy on 2012-05-24
I went into synaptic and completely deleted that file, problem still persists.

---

### Post by Plodder on 2012-06-04
I think that this is a video card problem.  I have the same problem when using the NVIDIA driver but not when using the Nouveau driver.

---

### Post by Plodder on 2012-06-04
I've just installed lo-menubar from the Ubuntu Software Center. I seems to have solved 90% of my problem.

---

