---
title: "Bash script: how to remove stupid dialog?"
date: 2011-03-13
forum: General Help
---

### Post by Kwijibo_Maverick_Meerkat on 2011-03-13
Hi

I wrote a bash script to mount the floppy drive in Ubuntu 10.10 (floppy drive bug) so I didn't have to keep typing ```
udisks --mount /dev/fd0 
```every time I wanted to view a floppy. So I wrote the script according to a tutorial, and saved it as "Getfloppytowork.sh" and edited the permissions so it was executable. But now I get the stupid dialog: 



[IMG]https://lh5.googleusercontent.com/_we4BhydUnCA/TXyMB1hlo8I/AAAAAAAAACg/oe6LKt3eNCI/Damn%20dialog.png[/IMG]

I want to make it so the file runs automatically on double click. Is this possible?

---

### Post by VCoolio on 2011-03-13
In nautilus (your file manager), go to edit > preferences > behavior tab. There you can set behavior for executables.

---

### Post by Kwijibo_Maverick_Meerkat on 2011-03-13
Thank you!

---

