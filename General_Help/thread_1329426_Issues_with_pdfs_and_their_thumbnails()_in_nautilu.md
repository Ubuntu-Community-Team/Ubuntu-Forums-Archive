---
title: "Issues with pdfs and their thumbnails(?) in nautilus"
date: 2009-11-17
forum: General Help
---

### Post by courtjester555 on 2009-11-17
**The problem:**

Folders (specifically, the Documents folder) containing large pdfs will not display those pdfs; the folder just continues to load. Note that these files will appear if moved to the desktop.

**The workaround:**

sudo nautilus does the trick. If I browse into my Documents folder with super user privileges, the pdfs appear instantly. From there I can cut and paste them onto the desktop, where they will appear instantly.


What is the issue here? Is it the thumbnail generator? Nautilus? Evince (it already leaks memory)?

---

### Post by ohzopants on 2009-11-17
There's a nautilus preference for setting maximum size for which files to generate thumbnails for.

Since it works for root (by the way, you should use gksu instead of sudo to run graphical apps) and not for you, and that these settings are set on a per user basis, this seems like a likely cause.

---

### Post by ethanay on 2009-11-19
It doesn't have to do with the size -- it happens even on small (<15kb) pdf files.  It appears to be a bug with how evince and  nautilus are interacting, but I don't know how to track it down further.

Sometimes, the entire contents of my folders disappear -- when this first happened my heart lept through my throat! (yes, I make backups...).

However, now I know I can go to file preferences, disable and then re-enable thumbnailing and it seems to temporarily solve the issue.

---

### Post by SirWeazel on 2009-11-25
I too am having this issue, and i'm also not sure how to track it down. I have a folder with .pdf files, under my documents folder.  When browsing to the directory nautilus appears to get stuck. When i run sudo nautilus i can browser no problem.  And i agree it is not the size of the files, because each file is only about 350K. I have 43 files in the directory now. I also can browse to the files from another program (such as uploading from firefox/opera).

Is there any type of files checking utiltiy to run an the directory that might correct the problem?  Is it nautilus or is it a problem with something else?

When i run nautilus from the terminal (not as sudo) i get the error "(nautilus:4788): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed"  Could this be something?

---

### Post by JBAlaska on 2009-11-25
Check the ownership on the directory or drive your keeping the pdf files in, does your login user own the dir or root?

---

### Post by SirWeazel on 2009-11-25
Yes, i thought that, and have checked.  Just to make sure, i brosed to the folder using gksu nautilus, right clicked, properties, permissions, and made sure the folder and enclosed files were mine.  Unless there is another/better way to do that to make sure.

---

### Post by ethanay on 2009-11-28
It is not an ownership issue.  The previewed files reappear if I go one folder deeper and then back into the folder whose files I wish to see.  Of course, this is a problem if said folder is the last in that directory!  Hitting "refresh" doesn't help.

I have only seen the problem with directories that have many PDFs in them

---

### Post by jonathane1980 on 2009-11-29
I have this issue as well. I dropped to terminal to move the files out of the document folder into my home folder. Once in my home folder, there was no longer a problem. If I make another folder and call it something other than "Documents," there is not a problem viewing the PDFs. However, if I delete the documents folder and rename the other folder Documents, the problem returns. I have created a separate folder for PDFs, and this work around seems to have resolved the issue for the time being.

I will submit a bug against nautilus unless someone else has already.

---

### Post by nowhere@cox.net on 2009-12-04
It's not just pdfs. I have the same problem with png, psd, and mp4 so far. I'll keep a tally and check launchpad for known bugs...

---

