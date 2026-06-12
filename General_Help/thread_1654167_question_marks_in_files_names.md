---
title: "question marks in files names"
date: 2010-12-28
forum: General Help
---

### Post by berzerke on 2010-12-28
I've got multiple files with question marks in the file name. Like this for example:

./CONESUP/UNIVERSIDAD CAT?LICA DE COSTA RICA.pdf

 I'm trying to rename the files to something else, but every attempt fails with a "No such file or directory" error. So far I've tried quotes, a backslash, quotes and a backslash, and several searches (google and here). I even tried to rm the file using the -- option. Can someone tell me how to get these files renamed?

---

### Post by noah++ on 2010-12-28
I am having no problem creating and manipulating files with question marks in their names. I am finding I don't even have to quote.

Are you remembering to escape the spaces as well?

If all else fails, try wildcards or a GUI.

**Edit:** It occurred to me that the question marks may be encoded as characters with accents and simply *displayed as *question marks because the terminal's doesn't know how to display the character*.* So ? is not really ?.

Anyway, you could also [rename based on inode number]("http://webcache.googleusercontent.com/search?q=cache:Qup1dbJ09o4J:labtestproject.com/linuxcmd/mv.html+mv+by+inode&cd=1&hl=en&ct=clnk&gl=us&client=ubuntu").

---

### Post by berzerke on 2010-12-28
Correct. I suspect the question marks aren't question marks at all. (Not my files, I just have to clean them up.)

I guess I've have to try the inode solution unless someone suggests something better.

---

### Post by tredegar on 2010-12-28
Try **utf8-migration-tool** It's in the repositories.

---

