---
title: "vncserver issue"
date: 2009-06-26
forum: General Help
---

### Post by kg87 on 2009-06-26
I've stumbled upon a tad of an issue.

I've worked with vnc for almost two years with just windows clients. however, I've since introduced ubuntu into my home network both VM and Full installation. Anyway happy story over. 

I've noticed I can quite happily view local and external hosts via vnc from ubuntu. But i've only just realised i cannot access the ubuntu pc via VNC.

I've (seemingly) setup the VNCserver for the Ubuntu share, set the password. I've tried the display as :0 and still nothing. Personally i think its just the lack of frontend for the server app. but could anyone shed some light?

Thanks

---

### Post by kg87 on 2009-06-26
[ATTACH]119078[/ATTACH]

Its i presume that it saying "others can access your computer using the address localhost". 

So is this not relaying the IP information to the vncserver?

---

### Post by kg87 on 2009-06-26
I'd like to mark this as solved, but can't find the drop down menu!

Solution : the Display was set as 10, which confused me no end!

---

