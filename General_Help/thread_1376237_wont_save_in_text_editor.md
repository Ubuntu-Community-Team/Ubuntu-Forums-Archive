---
title: "wont save in text editor"
date: 2010-01-08
forum: General Help
---

### Post by 3948ctyj on 2010-01-08
I try to name a file in the editor with this and nothing happens...?????



(creating a conky_start.sh file under home directory and add it to start up)

$cd && touch conky_start.sh && chmod +x conky_start.sh && gedit conky_start.sh

And add these lines to that file and save it :

#!/bin/bash
sleep 30 &&
exec conky -d -c ~/.conkyrc &
exit

---

### Post by Brandon Williams on 2010-01-09
The '$' in your example represents a command prompt. You should not actually enter it on the command line.

If you weren't typing that character on the command line, then we'll need some more information. Is there an error message presented when you enter the command line? Or when you try to save the file in gedit?

---

### Post by 3948ctyj on 2010-01-09
it took the filename and the code in it.....  well see if it works

---

