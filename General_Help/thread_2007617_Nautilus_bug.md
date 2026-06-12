---
title: "Nautilus bug"
date: 2012-06-21
forum: General Help
---

### Post by mrmedia on 2012-06-21
Absolutely positively the following.....
Firstly,
when dragging and dropping a folder (or menu copying) into another folder - a refresh copy - and existing structure is already there - the copy and merge fails to be performed on subsequent sub folders ; after you select "skip" for a file and "apply to all others". 
You do not get prompted to merge remaining folders. 
i.e. skip by implication has become "cancel".

On a programming perspective this is 101 on the dohhh scale. 

Secondly - after a while drag and drop are the only way to perform copies of folders and subfolders.  
The right click copy is still available but the other Nautilus will not offer a 'paste' option.  Something to do with bad memory management??????   i.e. right click the folder and "paste into folder".
Probably the same when a new tab child window is in the same nautilus - when the memory thing kicks in.

---

### Post by Zill on 2012-06-21
mrmedia:  I am sorry but I cannot see a question here.  If you are asking a question then please rephrase it.

If you think you have identified a new bug then please raise a bug report via Launchpad.  See [Report a problem]("http://www.ubuntu.com/community/report-problem") for further information.

---

### Post by mrmedia on 2012-06-21
Does anyone know how to get the writer of Nautilus to implement "copy" properly?
Does anyone know how to get the writer of Nautilus to implement "memory usage" properly so when 5 Nautilus are running the desktop does not crawl to a halt.
Has anyone found that the other filemanagers are better, I remember some I tried as being lesser than nautilus.
e.g, merge and copy subfolders.   e.g. having 5 open managers.

---

### Post by Dave_L on 2012-06-21
Why do you need five instances of Nautilus running at the same time?

Between the Extra Pane (Split Screen) feature and the New Tab feature, the only time I need more than one is when I need to run one as root.

---

### Post by Zill on 2012-06-21
> **mrmedia said:**
> Does anyone know how to get the writer of Nautilus to implement "copy" properly?
"Properly" is a subjective term.  Please give an example of what you have difficulty with.  Show the specific file structure eg.
[INDENT]DirectoryA
--file1
--DirectoryB
----file2
----file3
DirectoryC
--file4
--file5
etc.[/INDENT]
Explain what does not work for you using a similar example.
> **mrmedia said:**
> Does anyone know how to get the writer of Nautilus to implement "memory usage" properly so when 5 Nautilus are running the desktop does not crawl to a halt.
As Dave_L pointed out, there is rarely a need to run *five* separate instances of Nautilus!  However, I tested this and did not experience any problems.  Possibly your PC spec is inadequate to run multiple instances.
> **mrmedia said:**
> Has anyone found that the other filemanagers are better, I remember some I tried as being lesser than nautilus.
e.g, merge and copy subfolders.   e.g. having 5 open managers.
There are plenty of file managers out there - all with pros and cons.  One advantage of Linux is that they are all free and so you can try them out and see if they work for *you*.
Personally, although I often use Nautilus, I also use the "old fashioned" two-pane file manager [emelFM2]("http://packages.ubuntu.com/lucid/emelfm2") for some specific tasks (it's in the repos).

---

### Post by mrmedia on 2012-07-03
The example is in 1st message.

If you go to refresh a "tree" - you are prompted re" merge and again re:files - allowing "skip"

If you select skip - then all remaining subfolders are skipped too.

"skip" ought to be only files and only this folder.

All subsequent merges fail.
It is probably just an embarrassing logic error.
But significant enough to affect functionality.

---

### Post by mrmedia on 2012-07-08
yes thankyou, I will "report a bug" via appropriate channel. I just re-read that bit.

Also I will try emelfm2.  And maybe i ought to be try "midnight commander" that i recall now. 

So thanks.

---

### Post by mcduck on 2012-07-08
> **mrmedia said:**
> The example is in 1st message.

If you go to refresh a "tree" - you are prompted re" merge and again re:files - allowing "skip"

If you select skip - then all remaining subfolders are skipped too.

"skip" ought to be only files and only this folder.

All subsequent merges fail.
It is probably just an embarrassing logic error.
But significant enough to affect functionality.
In your first post you said you also clicked the "Apply to all others" check box.

Just don't do that and everything should work just fine. "Apply to all others" means exactly what it says, and applies the "skip" to all remaining files and directories. That's not a bug, that's the intended functionality of that option. (Much more useful when you are doing a replace instead of skip, though).

---

