---
title: "Remove Windows applications from Lubuntu right click 'open with' menu"
date: 2012-02-04
forum: General Help
---

### Post by Dennis N on 2012-02-04
When I right click on a file, a list of applications are offered to open it. However, since I have installed Wine, among those are unwanted choices such as "wine core.exe" and "notepad". In fact, "wine core.exe" is repeated 4 times in the same menu as a possible application to view a JPG file.

The 'file properties' for any these affected files has an 'Open with' list to set the default, but the drop down list also shows these windows applications as options, and I see no way to delete them.

How can Wine and Notepad be removed, and prevented from appearing as options?
 
Note: This is not about setting the default. The correct Lubuntu application is the default and opens the file when double clicked. I just don't these windows applications cluttering up the 'open with' list.

---

### Post by Toz on 2012-02-04
If you delete the file **~/.local/share/applications/mimeinfo.cache**, it will remove those entries. However, that file seems to get regenerated regularly. Not sure how to stop that from happening.

There is a wine bug report for this: [http://bugs.winehq.org/show_bug.cgi?id=27459]("http://bugs.winehq.org/show_bug.cgi?id=27459")

---

### Post by Dennis N on 2012-02-04
> **Toz said:**
> If you delete the file **~/.local/share/applications/mimeinfo.cache**, it will remove those entries. However, that file seems to get regenerated regularly. Not sure how to stop that from happening.

There is a wine bug report for this: [http://bugs.winehq.org/show_bug.cgi?id=27459]("http://bugs.winehq.org/show_bug.cgi?id=27459")

What about removing one or more of these .desktop files in there? Would that do it? Thanks.

```
dennis@Roxanne:~/.local/share/applications$ ls
mimeapps.list                wine-extension-jpe.desktop
mimeinfo.cache               wine-extension-jpeg.desktop
wine                         wine-extension-jpg.desktop
wine-extension-chm.desktop   wine-extension-png.desktop
wine-extension-gif.desktop   wine-extension-puz.desktop
wine-extension-hlp.desktop   wine-extension-rtf.desktop
wine-extension-htm.desktop   wine-extension-txt.desktop
wine-extension-html.desktop  wine-extension-wri.desktop
wine-extension-ini.desktop   wine-extension-xml.desktop
wine-extension-jfif.desktop 

```

---

### Post by Dennis N on 2012-02-04
OK, I renamed mimeinfo.cache to mimeinfo.cache.bak and that seems to have solved the problem. Thanks for the solution.

Marking as solved.

---

### Post by muppet317 on 2012-12-26
Brilliant, many thanks. Had exactly the same problem after removing wine and four versions of wine core exe appearing in the open with context menu. Renaming mimeinfo.cache did the job.

---

