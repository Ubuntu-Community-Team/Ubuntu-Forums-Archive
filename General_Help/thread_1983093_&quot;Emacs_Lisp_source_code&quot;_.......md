---
title: "&quot;Emacs Lisp source code&quot; ...... ?"
date: 2012-05-19
forum: General Help
---

### Post by grey1beard on 2012-05-19
I'm running 11.04 on a laptop on which I write G-code for my cnc machine.

I've been creating it in Gedit, and I've just noticed that, while most of the files, saved with an .ngc extention for the Linuxcnc software to use, are listed in my folder type column as "plain text document", some are now appearing as "Emacs Lisp source code".
This has only started as far as I can see by the date modified column in the last few days, and isn't consistent - some still filed as "plain text document".

However, I'd like to know where this behaviour is coming from, as I still create my files in exactly the same way as before, and always work from scratch, typing the code straight in, and saving as .ngc .

Can anyone enlighten me without going into the pros and cons of programming languages, or other exotica ?

Thanks,
John

---

### Post by Dave_L on 2012-05-20
I don't know if this helps, but this is from my notes:

> File associations:

~/.local/share/applications/

/usr/share/applications/

[http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-modifying.html.en](http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-modifying.html.en)

I would check those two directories to see if "ngc" is present and is associated with emacs.

---

### Post by grey1beard on 2012-05-20
Thanks for posting Dave, but the problem has been solved on the Linuxcnc forum from a suggestion by a moderator Jon Melson.

I often put a commented out text at the beginning of a file describing the contents before I have entered any code, and it seems that Gedit was interpreting this as a lisp code.
I took a file I needed to edit, and  moved the comments down, behind my usual first line of
G17 G21 G40 G49 G54 G80 G90 G94
and saved the file with a new name. Sure enough, it was saved as a plain text file.

Regards
John

---

