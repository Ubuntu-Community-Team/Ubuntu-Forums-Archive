---
title: "root when copy"
date: 2011-10-02
forum: General Help
---

### Post by jay_jay on 2011-10-02
Hello,
I can't copy a folder via file browser. The folder i want to copy contains files and folders which contain files and folders. I tried trough terminal and it worked partially because the files in the primary directory copied, but the subdirectories and their files didn't. Can someone tell me how to authoticate, so i can have root privileges when working with file browser?

---

### Post by spiky001 on 2011-10-02
Did you get permission denied errors, who,s folder and what folder is it.

---

### Post by carranty on 2011-10-02
I'm not sure I understand the problem, being root when copying won't make a difference, unless theres a file permission issue.  If I have a directory 'Bob' in my home folder and wish copy it to my Desktop I'd open a terminal and type

[I]cp -r /home/[username]/Bob /home/[username]/Desktop

[/I]That would copy everything in the folder.  Copying it via the file manager (nautilus I assume) should work also though.

Please be more specific if you're still having trouble.

---

