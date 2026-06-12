---
title: "how to define application to open a certain file type"
date: 2010-07-20
forum: General Help
---

### Post by DrScum on 2010-07-20
I have installed Gantt Project (project management application) under 10.04. The system identifies the .gan files produced by the program as xml files. 
How do I tell the system to open .gan files with the GanttProject application? 

I tried right click on the file to open and using "Open with other application" but the GanttProject application does  not appear to be in the list of available programs.

---

### Post by lykeion on 2010-07-20
I'm assuming you are using Nautilus when you right-click the files and selecting Open with other application...

In the dialog popup, have you noticed below the list of applications there's a line saying "Use a custom command"? 
You can click on it and then click Browse... to select your Gantt application launcher (i.e ganttproject.sh).

But like you said, .gan files are .xml files, so if you tick "Remember this application..." in the Open with-dialog, it means xml files will be opened with Gantt in Nautilus.

A final note is that this is not a system wide file association, it's only in Nautilus. 
If you're intersted in the details you can check these links:

[Packt Articles - Control of File Types in Ubuntu]("http://www.packtpub.com/article/control-of-file-types-in-ubuntu")
[Ubuntu Forums - File Association & Mime Types?]("http://ubuntuforums.org/showthread.php?t=383040")

Hope this will help you...

---

