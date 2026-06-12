---
title: "I don't know what I'm doing!"
date: 2011-12-05
forum: General Help
---

### Post by bill-lancaster on 2011-12-05
Some time ago I had advice from a forum regarding a start-up script.

I have "startup.sh" in my start-up applications.  It contains "#!/bin/sh".

How can I find the script that this invokes?

Thanks

Bill

Ubuntu 11.10

---

### Post by Lars Noodén on 2011-12-05
The script will be on the lines below the top line "#!/bin/sh"  If there is nothing there, then there is no script.

---

### Post by bill-lancaster on 2011-12-05
Thanks - but the mystery continues.  Will post again later

---

### Post by carranty on 2011-12-05
What exactly so you want the startup script to do?

A script is just a text file containing multiple commands, if the text file is blank (or just has the single entry #!/bin/sh, its not really a script at all.

---

### Post by aeiah on 2011-12-05
for clarification, that top line : "#!/bin/sh" is just a declaration that the script use the sh shell as it's interpreter. the path of sh is /bin/sh. another common one is the bash shell, and if a script needed to use that, it would have "#!/bin/bash" at the top.

---

