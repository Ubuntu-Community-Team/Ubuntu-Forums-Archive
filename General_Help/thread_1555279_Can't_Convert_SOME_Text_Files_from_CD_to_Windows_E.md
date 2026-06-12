---
title: "Can't Convert SOME Text Files from CD to Windows End-Of-Line (Permissions FINE!)?????"
date: 2010-08-17
forum: General Help
---

### Post by OzzyFrank on 2010-08-17
OK, this a new one for me, and was suspecting something happened to the **[COLOR="Red"]tofrodos[/COLOR]** command... but now not so sure. I have used that command (or the **unix2dos** part of it) a lot to convert the end-of-line from Unix/Linux to Windows/DOS, for files meant for Windows users (otherwise all they see is one big paragraph with black squares instead of paragraph breaks).

Being somewhat paranoid, I occasionally open a file or two to check (I convert a folder of txt files at a time), and do that simply by opening them in Gedit, going to Save As, and seeing what the End Of Line is there (I'd welcome a terminal command that could show me the end-of-line for files in a folder, if someone knows it!). And I never had any problems, until now.

Now, I will mention that these files in question are in fact copied from a CD backup, and I am aware of permissions issues that can arise from files copied from a disc (I've had to deal with that way too much in fact!). But this is the weird part, as when I run the command on a folder of txt files, half seem converted and the other half are still in Unix format. Correct me if I am wrong, but if it was a permissions/read-only issue, it would apply to ALL the files in the folder, not randomly working on some, and not on others.

Now. I've also confirmed the status of the files via Kate... and can change the end of line with it, apparently successfully, yet when I close and reopen the problem files in Kate, they're back to Unix format. As you can imagine, this is driving me nuts!

Now, create new files and paste the text in, save as usual (ie: default Linux end-of-line), THEN run the command, sure enough they are now converted to Windows. The originals stay unconverted.

Now, I have a few of these suspect files, so would rather not have to do this manually for each, and of course I'd rather find the answer for what is causing this. As I said, I doubt it is a permissions issue, because all other files seem fine, none read-only, all owned by me, and the majority of text files convert without issue.

If someone knows what the heck is going on here, I'd be glad to know. Cheers.

PS: For those who don't know, **unix2dos** is now **[COLOR="Red"]todos[/COLOR]** (or **fromdos -u**), and I even tried to force (-f) this, which should get around permissions issues anyway, with the command being:

**fromdos -u -f *.txt**

---

