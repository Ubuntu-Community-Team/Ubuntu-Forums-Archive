---
title: "PDF and pdf"
date: 2006-04-14
forum: General Help
---

### Post by manannan on 2006-04-14
When I try to open a PDF document in nautilus, I get the following message:

> The filename "irqs.pdf" indicates that this file is of type "pdf document". The contents of the file indicate that the file is of type "PDF document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "PDF document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.

I'm not sure how it happened; I may have installed a third-party PDF viewer that changed it, but anyway, will Ubuntu allow me to look at the list of registered extensions and modify it? I mean something like the 'File types' dialog in Windows.

---

### Post by dj-toonz on 2006-04-14
Hi , you can change the file type by right clicking on the file , going down to propities , open with , then selecting the program u want to open the pdf with i.e i use adobe acrobat reader so that's in the listing, put a mark in the box then click on close , job done. but if the program isnt in the list , you can add it yourself by clicking on add then searching for the program i.e in the list what appears or a custom comand then click on ok 

Hope that helps

---

### Post by manannan on 2006-04-15
Not really, but thanks anyway. It already has the association, but Nautilus won't let me open the file. I'm not sure how it works, but maybe I should change the extension's associated MIME type. I thought Gnome had a 'Files and Programs preferences tool', but I can't find it in Ubuntu.
Oh well -- I got around the problem by renaming my .pdf files to .PDF .

---

### Post by peterwr on 2006-07-28
Hi, manannan

I don't have a solution, I'm afraid (other than using the right-click menu to open the files, which would have saved you renaming them), but you might like to keep an eye on this thread:

[http://www.ubuntuforums.org/showthread.php?t=224064](http://www.ubuntuforums.org/showthread.php?t=224064)

To see if anyone comes up with a response there. 

HTH

Peter

---

### Post by parktownprawn on 2006-09-20
I had that problem too.

I think it has to do with the old .desktop files in your home directory. They are created when you customise the gnome-menu and by various other programs which modify your gnome-menu.

look in the subdirectories of
```
~/.local
```

I think these may be conflicting with nautilus. If you find the right file to edit/delete you can fix this problem. The problem is probably with evince.desktop

I was lazy and just deleted the whole ~/.local directory.

This had the side effect of destroying the customisations i had made of the gnome menu but it fixed this irritating problem.

---

### Post by glaucus on 2006-09-30
Don't just delete directories willy-nilly. If you move ~/.local/share/mime to ~/.local/share/mime.old you get the desired effect. I'm not sure what is going on to make this happen, but this is a quick (safe) fix.

---

