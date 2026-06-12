---
title: "from running sudo rm bin/sh!!"
date: 2011-04-07
forum: General Help
---

### Post by raw937 on 2011-04-07
Hello,

I ran this command
for this other program SOrt-ITEMS


sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh

NOW, I am having all types of problems

Get this error for firefox:
Failed to execute child process "firefox" (No such file or directory)

Get this error for openoffice:
Failed to execute child process "ooffice" (No such file or directory)

And this in command line:
bash: /usr/bin/lesspipe: /bin/sh: bad interpreter: No such file or directory


WTF, which program is next!!!!!!!!!!!!!!!

---

### Post by wolfen69 on 2011-04-08
In the future, **rm** means remove. If you are not sure what you're doing, come here and ask first.

---

### Post by jerome1232 on 2011-04-08
Well normally it links to dash, you could probably just remove the current link you have and link it back to /bin/dash.

I believe your supposed to use the command chsh normally to change shells. I've never really played with other shells though so ymmv.

---

