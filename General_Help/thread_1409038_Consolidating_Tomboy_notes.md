---
title: "Consolidating Tomboy notes"
date: 2010-02-17
forum: General Help
---

### Post by afrodeity on 2010-02-17
Bit of a problem. I have two completely different sets of tomboy notes. The one .tomboy folder is on a working machine. The other is on a machine which no longer works. 

I need to consolidate the two .tomboy folders, unfortunately the notes are both numbered the same way although they have different content. 

In other words simply cutting and pasting the notes results in a conflict. Is there a safe way to bulk renumber the old notes and import them into my new .tomboy folder so that they will show up? I don't want to simply dive in and do this manually since Tomboy has a very specific method of numbering the individual notes. Any clues, suggestions?

---

### Post by coldraven on 2010-02-17
I don't know for sure but what is the note import tool for?
Maybe some info on their web-page.
See the attached screenshot

---

### Post by afrodeity on 2010-02-17
That would be the sticky note importer for importing notes from the sticky note application. You can access sticky notes by right clicking on panel and choosing add to panel. It's a totally seperate application. I need a **Tomboy Notes importer.**

---

### Post by afrodeity on 2010-02-17
This is a PIM importer script for Tomboy
[http://www.movingtofreedom.org/2008/02/23/tomboy-bulk-import-files-with-the-dbus-interface-and-python/](http://www.movingtofreedom.org/2008/02/23/tomboy-bulk-import-files-with-the-dbus-interface-and-python/)

---

### Post by scarpent on 2010-02-17
That's my post at movingtofreedom.org -- thanks for the pointer, but I wanted to mention that the script there is meant for importing flat files.  If you try using it to import tomboy files, you'll get a bunch of XML.  I'm guessing you could use the D-Bus API to do something along this line, and also guessing there are easier ways to do it.

---

### Post by sharm on 2010-02-17
Your best bet is to:

[LIST=1]
[*]quit Tomboy
[*]open the *.note files that you want to import in your favorite text editor
[*]edit the title to something unique (note that there are two places where you must change the title)
[*]copy the unique-ified *.note files into your existing Tomboy note directory
[*]start Tomboy, and everything should Just Work
[/LIST]

---

### Post by afrodeity on 2010-02-19
You mean change the file name? They would need to have unique file names which don't conflict with the files that tomboy has already assigned. I could just try adding a digit to each of the files and see what happens?

---

### Post by sharm on 2010-02-19
You should not need to change the file names.  The file names are completely different from the titles, and should be totally unique unless you have copied note files around manually.

I'm talking about changing the title inside of the XML itself.  Since you talked about your notes being numbered the same way, I assume you mean that each collection has its own, separate "New Note 2", "New Note 3", etc.

So you would just need to modify the titles seen in the notes.  For example, here's an excerpt from one of my note files:

```
<note version="0.3" xmlns:link="http://beatniksoftware.com/tomboy/link" xmlns:si
ze="http://beatniksoftware.com/tomboy/size" xmlns="http://beatniksoftware.com/to
mboy">
  <title>New Note 60</title>
  <text xml:space="preserve"><note-content version="0.1">New Note 60

Describe<link:broken> your new</link:broken> note here.
```

You would need to change both places where "New Note 60" occurs to effectively rename the note.  Changing the file name should be completely unnecessary.

---

### Post by afrodeity on 2010-02-19
Well that is the problem I have two sets of notes, both with the same or similar "random" file names. So can't copy the one set into the other folder. Problem is not with the contents but with the file structure.

---

### Post by sharm on 2010-02-19
> **afrodeity said:**
> Well that is the problem I have two sets of notes, both with the same or similar "random" file names. So can't copy the one set into the other folder. Problem is not with the contents but with the file structure.

The only way you could possibly have identical file names is if you had previously copied the files between the directories, which would imply that they are probably identical notes.

I'd recommend opening them up, and if there are any differences, pick the one that has the right contents.  If you need help looking for differences, a graphical diff tool like Meld might be helpful.

---

### Post by afrodeity on 2010-02-19
Okay,I think the problem is that I copied the notes across earlier, and forgot about it, but they not showing up in Tomboy. For example, there are 26 notes listed but 55 notes in the folder. So do I need to "uniquify" the content for them to show up as per your earlier posting?

---

### Post by sharm on 2010-02-19
> **afrodeity said:**
> Okay,I think the problem is that I copied the notes across earlier, and forgot about it, but they not showing up in Tomboy. For example, there are 26 notes listed but 55 notes in the folder. So do I need to "uniquify" the content for them to show up as per your earlier posting?

It's possible.  Tomboy acts unpredictably when multiple notes share the same title, so if you have that problem it could be causing your issue.  But it could also be something else.  The only normal thing I can think of is that if you have a ton of notebooks, the template notes would not show up in the list, and might account for the discrepancy.

If you are comfortable sharing your notes with me (the upstream Tomboy maintainer), please zip up your note directory and mail it to [email]sanfordarmstrong@gmail.com[/email], and I'll take a look. It should save you a bit of time.

---

