---
title: "Apache htdocs &quot;nobody&quot; login"
date: 2010-07-31
forum: General Help
---

### Post by atmega-ist on 2010-07-31
Hello, all -

I'm hoping that this is, indeed, a "general" issue and I'm not over-thinking anything but long story short - I can't get my Apache htdocs folder to accept any files without copying via sudo through the terminal..  Also, when viewing a page over my network I'm just seeing the raw text/code for the file and not the intended output.

I'm assuming that logging in as "nobody" (current owner of htdocs) would allow me to drag/drop/edit files in the htdocs folder itself but I can't for the life of me deduce what the password is for "nobody".  Is there a universal default?  The security issue posed by such a default does, however, make me think this is something I possibly set up during installation and forgot about?

I just want to be able to navigate to my htdocs folder when creating/editing a file and to be able to interact with the folder outside the terminal.

Thanks!

---

### Post by gordintoronto on 2010-07-31
Change the owner: 
man chown

---

