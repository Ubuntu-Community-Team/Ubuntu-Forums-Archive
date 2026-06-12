---
title: "Edit terminal preferences without the terminal"
date: 2011-07-10
forum: General Help
---

### Post by fhgshfdg on 2011-07-10
Hello fellow Ubuntuers. I did a very dumb them just now. I opened my terminal preferences window and chose to "run a custom command instead of my shell"

I ran a cat command to a text file, and now every time I try to open bash. It just closes automatically. How do I fix my terminal without my terminal? How can I get to the terminal preferences?

Thanks in advance!
      ](*,)

[IMG]http://i54.tinypic.com/71o5ts.png[/IMG]

---

### Post by matt_symes on 2011-07-10
Hi

Use gconf-editor to edit the profiles under /apps/gnome-terminal/profiles and remove the custom command.

Kind regards

---

