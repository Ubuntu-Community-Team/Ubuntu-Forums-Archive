---
title: "Strange message when using gnome-terminal."
date: 2010-05-17
forum: General Help
---

### Post by zozza on 2010-05-17
Hello,

For some reason whenever I load gnome-terminal using 9.10 I get this message:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

It started today - any ideas why?

Thanks!

---

### Post by Mountaineer on 2010-05-17
The first time you run a sudo command a touch file is created (an empty file that does nothing more than exist as a name) called .sudo_as_admin_successful.
It's hidden and it just sits there in your home directory.
You could either create it like this:
"touch .sudo_as_admin_successful"
or you could run a sudo command and sudo will do it for you:
"sudo ls".

Do one or the other and the sudo hint will go away. :)

---

### Post by zozza on 2010-05-18
Thanks - I found the touch file.

But what I don't understand is why after several months of using gnome this message appeared for the first time?

---

### Post by Mountaineer on 2010-05-18
Your guess is as good as mine.
Perhaps it was related to an update in some way. Or you accidentally deleted the touch file. <shrug>
Hopefully it doesn't pop up again. :)

---

### Post by doas777 on 2010-05-18
perhaps you got an updated gnome-terminal? or as a new user?

---

