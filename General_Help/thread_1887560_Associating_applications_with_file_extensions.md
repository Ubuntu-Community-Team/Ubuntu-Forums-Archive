---
title: "Associating applications with file extensions"
date: 2011-11-27
forum: General Help
---

### Post by dgoddard1 on 2011-11-27
I recently installed Ubuntu 10.04.3 and have used previous versions.

I have never found how to control the ability to associate a given file extension with a preferred application to open that file.

**BUT ........** 

Somehow the file extension ".pgp" appears to have become linked to the file browser so that, clicking on any file ending in ".pgp", brings up the error message: 

[B]Could not display "xxxxxxxxxx yyyyyyyy.pgp
The location is not a folder[/B]
  
where xxxxx is the path and yyyyy is the filename prior to the pgp extension.

I have been trying to get Ubuntu to utilize my pgp files

I would like to get Ubuntu
**A.**
-- to stop trying to use the file browser for opening pgp files and giving me this error message
**B.**
-- decrypt pgp files by prompting me for my pgp password when they are encountered.
**C.**
-- to use gimp as the preferred application to open image files.

Help will be appreciated.

---

### Post by MG&amp;TL on 2011-11-27
Gimp I believe can be set under 'default applications' in the system bar.

Go right-click, "open with", find your program. (I'm actually using PCManFM at the moment, so I can't test, sorry)

I'm not sure that you can ask for your password for pgp. You can use gpg and use gpg --decrypt at the command-line...if that helps.

---

