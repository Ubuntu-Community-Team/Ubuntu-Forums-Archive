---
title: "Google Sketch Up not starting in &quot;wine&quot;"
date: 2010-11-21
forum: General Help
---

### Post by arvevans on 2010-11-21
Google SketchUp won't start in wine.

[INDENT][IMG]http://qrp.webhop.net/Google_SketdhUp_Error.png[/IMG][/INDENT]

What is missing.  I think I have installed all the relevant GL things from the repositories.

Any help or ideas will be appreciated.

---

### Post by arvevans on 2010-11-21
Now marked as SOLVED.
I should have done some Google Searches before posting.  I found the answer on the bug list:

[INDENT]"bug 14045: If you get the error "SketchUp was unable to initialize OpenGL!], run regedit, open HKEY_CURRENT_USER\Software\Google\SketchUp6\GLConfig\Display, and change HW_OK to 1."[/INDENT]

It has been so long since I did much with Microsoft that I had totally forgotten about regedit tables.

Now SketchUp loads and runs perfectly.

---

