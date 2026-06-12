---
title: "Document Viewer &amp; .cbz bug"
date: 2011-02-23
forum: General Help
---

### Post by jamesisin on 2011-02-23
If the folder path to a comic book archive file (.cbz at least) contains an open square-bracket ([), Document Viewer will not be able to open the file claiming the document only contains empty pages.

This is not the case if the file name contains the opening bracket.

The same file as zip (cbz and zip are the same files just using different extensions) opens as expected (Archive Manager).

Image files (.jpg for example) open as expected in the same folder path (Eye of Gnome).

Portable Document (.pdf) files open as expected in the same folder path (Document Viewer).

Can anyone confirm this behavior?

Can anyone direct me to the best place to file a bug report?

Thanks.

(I tested this on 9.10 (works properly) and 10.04 and 10.10 (broken as described above).)

---

### Post by An Sanct on 2011-02-23
This seems to be the behaving of the application, you use to open comic books (also archives). Contact the author. If this is *comix*, then here is the [contact info]("http://comix.sourceforge.net/contact.html").

---

### Post by jamesisin on 2011-02-23
I'm sorry if my original post did not make this clear, but the misbehaving application is Document Viewer.  This is the standard Gnome viewer for (among other things) portable documents and comic book archives.

---

### Post by An Sanct on 2011-02-23
Oh :) sorry, if it is a part of software bundled with the default Ubuntu install, then [launchpad]("https://launchpad.net/") is the place to go post the bug ...

---

### Post by jamesisin on 2011-02-23
Were you able to confirm the bug?

Also, I am not able to find a filing link on this page:

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

---

### Post by An Sanct on 2011-02-23
Yes, I have found and downloaded a *cbz* file and can confirm this on maverick (10.10), Document Viewer 2.32.0

---

### Post by An Sanct on 2011-02-23
The application states, that it is a part of the [evince project]("http://www.gnome.org/projects/evince"), also for [launchpad]("https://launchpad.net/") you have to be registered and logged in.

---

### Post by An Sanct on 2011-02-23
The same happens if you put a *star* '*****' into the folder name, alltho the folder name is correct / acceptable, it says, that the comic book archive is empty.

---

### Post by jamesisin on 2011-02-23
I am a long-time registered member of launchpad.  However, I am not able to find a link for submitting a bug report.

Yeah, I was guessing it was failing to handle special characters correctly (not quoting something properly or failing to include \ or some such), so it's no surprise to find that the asterisk is also causing problems.

Thanks.

---

### Post by An Sanct on 2011-02-24
I also wanted to report some bugs, I all had them pinpointed and with a solution ready ... but the reporting mechanism tended to say "no need to report a bug" or something like that, anyhow, I was also unable to report it ...

Also I cannot get launchpad's email, confirming my registration :( ...

[Here is the official stuff...]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by jamesisin on 2011-02-24
Bug report filed:

[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/724429](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/724429)

I also wanted to point out that it seems that the bracket can appear anywhere in the folder path and not merely in the containing folder.

This:

```
/test\ \[/testing/book.cbz
```

Will fail just as this:

```
/test\ \[/book.cbz
```

---

### Post by Dennis Sheil on 2011-03-04
I saw this bug in Launchpad.  It is a problem, and even the latest version of evince has the problem.  I have notified the evince maintainers about the problem.  I see where the problem is, but don't have time to fix it at the moment.

---

### Post by jamesisin on 2011-03-04
I'm sure they will appreciate any information you are able to give them toward a solution.

---

