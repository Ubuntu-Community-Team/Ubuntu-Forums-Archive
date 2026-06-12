---
title: "Openoffice file lost"
date: 2012-03-10
forum: General Help
---

### Post by Charles_B on 2012-03-10
Hello,
I have a problem. I was writing in an openoffice file, when I lost power on my laptop. I was saving regularly, but when I started the computer again, the size of my file was 0 bytes. When I tried to open it first asked for ASCII, than it said it is locked for editing by unknown user and when I open it in read-only it is empty. (It is empty even if I open it with gedit).

Can anyone instruct me on how to recover my file? 
Thank you
PS. I have ubuntu 10.04[FONT=Times New Roman, serif]
[/FONT]

---

### Post by Vaphell on 2012-03-10
things don't look too good, to say the least :/
in case if you had automatic backups enabled (i don't think it's the default, look for it in OO preferences), navigate into .openoffice.org dir in your home dir (ctrl+h to unhide) and look there.

And remember to do manual versioning from time to time in the future (save as..., my_doc1, my_doc2, my_doc3), so if some accident happens you have something to fall back on. Having single instance of important document is not too smart no matter how you slice it.

---

### Post by Charles_B on 2012-03-10
I have auto-backup enabled, but the backup folder is empty. Does it empty every time you restart your computer? Well, good thing is I didn't loose much... I am backuping  my files regularly. Still, it is annoying to lose even an hour or two of work just because you loose electricity.

---

### Post by Charles_B on 2012-03-10
Or is there any "restore to previous version" (like in Windows) for Ubuntu?

---

### Post by Mark Phelps on 2012-03-11
> **Charles_B said:**
> Or is there any "restore to previous version" (like in Windows) for Ubuntu?

This is a KNOWN bug in OO -- I had it trash a document I was working on, just like with yours.

And no, there is no recovery option. I even had auto-save turned on, and it did not help. Sorry.

What I did was the following:
1) Recreated the document
2) Periodically saved a COPY to another location
3) When the original document got trashed, copied back from the other location.

---

### Post by kurt18947 on 2012-03-11
Mark, I've been following this and the last I knew it appeared to be a combination of OO/LO and ext4 file system.  Do you know if this bug occur in other file systems as well?  I've been saving backups to a flash drive (fat32).

---

### Post by Hagar Delest on 2012-03-13
Sadly, nothing to do: [22 page term paper replaced with pound signs](http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=17677).

Check the temporary folder of the system (see in OOo Tools>Options>OOo>Paths). If there are folders like sgmlf.tmp with a file having the same name inside, make a copy of that file, rename it in .odt and cross your fingers.

What OOo version BTW?

Else, nothing to do I fear.

---

