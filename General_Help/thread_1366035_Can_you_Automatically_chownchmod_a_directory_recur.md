---
title: "Can you Automatically chown/chmod a directory recursively?"
date: 2009-12-27
forum: General Help
---

### Post by jsfour on 2009-12-27
So here is the situation, I am trying to setup a folder so that everything that is added to it automatically becomes owned by a certain user. Additionally I would like to change the privileges of the files that I put into this directory.

Currently, every time I move something into the folder I must chown and chmod the new files. Is there a way that I can have the system make any files added to this directory have certain privileges?

---

### Post by abeisgreat on 2009-12-28
EDIT: Whoops, misread your question, I don't think thats possible, but I'm probably wrong.

---

### Post by falconindy on 2009-12-28
Look into inotifywait. You can have a watch script that runs in the background that would look something like....
```
inotifywait -qm --event CREATE --format %f /path/to/watch | while read file; do
  chmod ### "/path/to/watch/$file"
  chown xxxxx:yyyyy "/path/to/watch/$file"
done
```
You could start something like this from /etc/rc.multi.

---

