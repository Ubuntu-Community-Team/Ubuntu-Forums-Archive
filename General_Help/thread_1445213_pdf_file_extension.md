---
title: "pdf file extension"
date: 2010-04-02
forum: General Help
---

### Post by davesmith on 2010-04-02
Hallo
Could someone plz explain how to make sure that when I save a pdf file, the file extension .pdf appears in the filename? Its a silly little thing, but annoying. The file browser recognises it afterward as a pdf file though, it opens with document viewer ok.

Thanks

---

### Post by dcstar on 2010-04-03
> **davesmith said:**
> Hallo
Could someone plz explain how to make sure that when I save a pdf file, the file extension .pdf appears in the filename? Its a silly little thing, but annoying. The file browser recognises it afterward as a pdf file though, it opens with document viewer ok.

Thanks

You do **not** make a file a PDF file just by giving it a .pdf extension - only Windows allows such silly things.

Linux files have something called a "Magic Number" which determines what sort of file it is, and the app that saves the file usually sets that.

Only PDF creator programs can make PDF files, and they all usually automatically append the .pdf suffix.

---

### Post by gradinaruvasile on 2010-04-03
What do you use for pdf creation?

---

### Post by davesmith on 2010-04-03
I was not using any program to create the pdf. Its when I d/l one from a website, the file manager wont include the .pdf extension. So when I put the file on a memery stick and transfer to to a Windows m/c, windows cant recognise it as a pdf unless i rename it.

---

### Post by gradinaruvasile on 2010-04-03
File manager? Or is it the browser? AFAIK you can specify file name when you d/l anything.
In Firefox go to Edit -> Preferences and select "Always ask me where to save files"

---

### Post by davesmith on 2010-04-03
Right! I did Edit/Preferences/select place to d/l no prob. Its just that it wont include the .pdf extension in the filename. Try it yourself!

Im using Firefox 3.6.3 to d/l the file, when i look at the file in Gnome there is no file extension .pdf. Yet Document Viewer sees it as a pdf and opens it correctly. But because it dont have the .pdf extension, windows cant see it

I'm on Hardy btw

---

### Post by Chronon on 2010-04-03
You're saying to save it with a .pdf suffix and it's being saved without it?

---

### Post by davesmith on 2010-04-03
yes thats exactly whet happens, no suffix when saved....ive tried a lot of things to solve this issue and finally turned to the forums, it must be summat silly

---

### Post by gradinaruvasile on 2010-04-03
So you manually append the suffix?

---

### Post by t0p on 2010-04-03
When you are downloading a file, when it asks you where to save the file to, it will want to know what name to give the file.  It will generally supply a suggestion, but you can change it to whatever you like.  This is your opportunity to give the file the extension you like.  Look at the attached screenshot: it's suggesting I name the file "Google.html" but I can change that to anything I want, file extension included (or not included, if you like).

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=152240&stc=1&d=1270291371[/IMG]

For files you've already owned: in nautilus (file manager) right-click the file in question and select Rename.  Now you can rename the file, including file extension.

---

### Post by davesmith on 2010-04-04
Yeah thanks, i sorta worked that bit out myself and its a nice screenshot. Manually adding the suffix solves the prob, but its time-consuming. Is there a script somewhere I could run and add the .pdf suffix to about 80 files that need renaming? 

Regards

Dave

---

