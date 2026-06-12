---
title: "Evolution #inbox file"
date: 2010-08-11
forum: General Help
---

### Post by Zarckon on 2010-08-11
I've been using Evolution for several years no without problem. Yesterday I started getting the message "Error while opening home/name/.evolution/mail/local#inbox".

The mail is all there in local/inbox.sbd, but I can't find any way to tell the program this. I've got it all backed up on Dropbox, but can't find any trace of a #inbox. At least nothing with that name that's been recently deleted.

Is there some way of recreating or recovering the file I need?

Thanks for any help you can throw my way.

---

### Post by Zarckon on 2010-08-13
> **Zarckon said:**
> Yesterday I started getting the message "Error while opening home/name/.evolution/mail/local#inbox".

Actually I noticed that the error actually reads "Error while opening mbox:home/name/.evolution/mail/local#inbox".

Please anyone, help. I can't send or receive email through the evolution client any more. And can not access any of my old email (though it is clearly there in the folders). No obvious way to tell the program where the mail is. The import function doesn't work unless some other program that it recognizes has settings to import.

Help.

---

### Post by Zarckon on 2010-08-13
Okay, I found a solution for anyone who may have the same problem in the future (assuming that you have any chance of finding this thread). I found that when I renamed my mail folder that a new mail folder was created. This solved the problem, but as I recovered files from the renamed folder to the new one I discovered that actually the only file that needed to be replaced was the folder.db file. Apparently the database file had become corrupted in some way. It is automatically recreated on destruction, and very nice, was able to find all of the old mail folder categories and emails within them.

---

### Post by hubiedo on 2010-08-20
i am currently getting the same error. i will try your solution. thanks for posting the problem and solution

---

### Post by hubiedo on 2010-08-25
thanks zarckon,

i tried what you suggested but not really the answer i needed. 

i found that i had to copy the .evolution file folder to newfile name and reinstalled evolution fresh then i imported all of my previous emails form the newfile. i had to do the config all over again but i didn't lose everything so that is a plus for me. you were right it was something in the config but i never was able to figure out what was doing it. probably not the greatest solution but it worked for me.

---

