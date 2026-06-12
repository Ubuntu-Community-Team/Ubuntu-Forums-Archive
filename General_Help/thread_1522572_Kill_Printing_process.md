---
title: "Kill Printing process"
date: 2010-07-02
forum: General Help
---

### Post by PDA1 on 2010-07-02
How do I stop a printer from printing?

Here's what happened-  I started to print some PDF stuff and then changed my mind.  The printing job hadn't finished so I just clicked on the printer icon and selected QUIT.  Well, of course that didn't work so I just turned the printer off......same result- when I turn the printer back on it keeps on printing the same stuff.


How do I stop the printer from continuing and delete all print jobs?

---

### Post by cjtemple on 2010-07-02
Give this a shot. From the desktop goto
System -> Administration -> Printing
Select your printer and Press CTRL+F to view the printer queue
You can then select your document and delete it from the queue.
 
 
Alternatively from the CLI use
> lpq to display the queue
then
> lprm JobID to kill the job

---

### Post by PDA1 on 2010-07-02
Brilliant!

Thank you.....it worked perfectly (I had to just do a refresh on the document queue).

---

