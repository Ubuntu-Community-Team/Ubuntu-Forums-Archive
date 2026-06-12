---
title: "File encryption.. ?!"
date: 2010-06-01
forum: General Help
---

### Post by Killer Cop on 2010-06-01
I wanted to lean how to encrypt files and folders, and I managed to install Seahorse and get it working so I can right-click files and then encrypt them with a GPG key.. Working fine!

But there's one thing I simply don't understand. To open the file I have to enter the password, of course. But by pressing the delete button, I can erase the encrypted files. Not so secure again?

Why can I delete encrypted files? Doesn't make sense. :confused:

---

### Post by JustinR on 2010-06-01
It does make sense. Encrypting files is what is says it is to be. All It does is scramble the file contents so there unreadable without a password. This does not make your files invincible. The encrypted files can be deleted, copied, moved, etc. like any other file or directory you have.

---

### Post by WorMzy on 2010-06-01
I think you're misinterpreting the meaning of secure here. It's secure in that nobody can read the contents without a password, not secure in that it's fixed to the disk. If you want to make it harder to remove a file, then set it's owner to root and set file permissions to 755. (root has full access and can delete, but all groups can only read and execute)

---

### Post by Killer Cop on 2010-06-01
Okay, I see. Thanks for the help!

And thanks to you WorMzy for pointing out the root and permission stuff, gotta play with that some day.

---

