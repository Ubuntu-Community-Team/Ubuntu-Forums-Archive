---
title: "capture the information on the terminal to a file"
date: 2010-06-04
forum: General Help
---

### Post by murali026 on 2010-06-04
Hi,
   I have some output on the console on the gnome-terminal.
Could you please tell me how to log them in to a file...

Best Regards
murali026

---

### Post by dino99 on 2010-06-04
your command > myfile

---

### Post by Buuntu on 2010-06-04
[command] > file
That will write the output of the command to the file.  If the file already exists, the data will be overwritten.

If what you want to do is append to a file without deleting the data that is already in it, then you use '>>' instead of '>', like so:
[command] >> file

---

