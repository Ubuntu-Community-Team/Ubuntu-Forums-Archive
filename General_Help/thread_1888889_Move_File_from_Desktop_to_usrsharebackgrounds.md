---
title: "Move File from Desktop to /usr/share/backgrounds"
date: 2011-11-30
forum: General Help
---

### Post by Richiegs on 2011-11-30
I tried to move a file on the desktop to /usr/share/backgrounds by using the following command in the terminal:

sudo mv <filename> /usr/share/backgrounds

The response I got was "No such file or directory."

Did I use the above command correctly?
Why did it come as "No such file or directory?"

Thank you

---

### Post by stinkeye on 2011-11-30
sudo mv ~/Desktop/<filename>  /usr/share/backgrounds

Because you haven't put the path it's looking in your home folder.

---

### Post by Richiegs on 2011-11-30
> **stinkeye said:**
> sudo mv ~/Desktop/<filename>  /usr/share/backgrounds

Because you haven't put the path it's looking in your home folder.

Thank you

---

