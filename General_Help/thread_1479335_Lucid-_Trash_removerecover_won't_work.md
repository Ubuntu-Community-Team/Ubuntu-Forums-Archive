---
title: "Lucid- Trash remove/recover won't work"
date: 2010-05-10
forum: General Help
---

### Post by de Bacon on 2010-05-10
I mistakenly moved a folder to the trash where it is stuck.  I have tried moving it back to its original location using 2 methods, drag and drop, menu -edit- move.  I also tried moving the files within the folder out individually though I get the same message.

When trying, I get an error message 
> **Error while copying "mlmeTypes.rdf"**

There was an error copying the file into media/(location)/(file name).

Show more details

Items in the trash may not be modified

I am glad it isn't something important! not this time at least.

---

### Post by upbeat.linux on 2010-05-10
My guess is that mimetypes.rdf was deleted from your Firefox profile.  I'm guessing either 

1. You don't have permission to purge the file.  You'll need to change the permissions on it.

or

2. Firefox still has a lock on the file and you'll need to close Firefox (possibly kill processes) before deleting it

---

### Post by de Bacon on 2010-05-10
This is just totally weird!  I gave up, but then came back after receiving this post, **now it works** It was not just a firefox file.  What ever, just a glitch that now seems gone!

Thanks for the thought :)  I don't understand what happened. It is fine now, odd.

---

### Post by upbeat.linux on 2010-05-11
Great!  It might be helpful if you were to include what application this belonged to or the original file path should another user experience the same issue.  Thanks

---

### Post by de Bacon on 2010-05-11
> Great! It might be helpful if you were to include what application this belonged to or the original file path should another user experience the same issue. Thanks 

There were two things, one was a firefox folder, did it when doing backup.  The other was a plain text document file.  Now I believe the whole thing was caused by firefox, a lock because I had firefox open when I was moving files, a no no but I was spacing on correct procedure. I knew better than to do backup with the program open.  But then in testing I moved the text file into the trash, another mental error (had a bad thought process day) and couldn't retrieve it then in that moment either, thus I thought there might be an err with the trash can.  It was the first time I used trash post upgrade to 10.04.

All is well now, I think? when I can that is!

---

