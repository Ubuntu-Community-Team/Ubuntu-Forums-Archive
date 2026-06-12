---
title: "Display BOM in less"
date: 2010-11-05
forum: General Help
---

### Post by danduq on 2010-11-05
This may not be the right forum for this question, but if anyone knows I'd be grateful.

I have a text file with a BOM in it (I can tell it's there from opening it in Hex Editor and seeing the "EF BB BF" at the beginning).

When I view the file from the command line using less, I cannot see it. If I scp the file to another server and view it in less there it shows up as <U+FEFF> at the beginning of the file.

There is obviously some environment variable or charset I need to configure, but I can't figure it out from the less man pages.

Thanks!

---

### Post by gmargo on 2010-11-05
It may have to do with **less** related environment variables.  The default **.bashrc** invokes the **lesspipe** program to set these variables.  Check your environment with "env | grep -i less".  You may see  **LESSOPEN** and **LESSCLOSE** variables.  If you have them, try unsettting them and trying **less** again.

---

