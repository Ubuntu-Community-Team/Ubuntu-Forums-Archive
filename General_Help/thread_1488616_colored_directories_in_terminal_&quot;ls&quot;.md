---
title: "colored directories in terminal &quot;ls&quot;?"
date: 2010-05-20
forum: General Help
---

### Post by BklynKid on 2010-05-20
Hi there.
Over SSH when I do a "ls" command, I see some directories with a green background and blue text. What does this mean?

I think it's related to a problem I'm having. I have the directories shared over the network. I'm the owner of all the directories but when I tried to move one of the colored directories to a different location (over the share from MacOSX) I got a generic "access denied" error. Any ideas?

Thanks!

---

### Post by SlugSlug on 2010-05-20
ls -l

may give you a better idea

---

### Post by BklynKid on 2010-05-20
"ls -l" doesn't tell me why it's green. What does the green highlight mean?

---

### Post by srs5694 on 2010-05-20
I haven't checked the configuration files, but I believe the green background for directories indicates directories that have world write permission.

Your "access denied" error could have been caused by ownership issues on one or more files or subdirectories *within* the directory in question. Try using "ls -ld" to view the full ownership and permissions on the files and directories in question.

You can also get "access denied" errors on the target side. If you don't have write access to the directory to which you're trying to move files, you won't be able to copy them. If the target filesystem doesn't support Unix-style ownership and permissions, you'll also get errors if you use a copying method that would change ownership or permissions; however, the error will read "operation not permitted," at least for "cp -a" command (it might say "permission denied" for some methods, though).

---

### Post by BklynKid on 2010-05-20
Thanks that helps.

When I did "ls -ld" it lists me as the owner with drwxrwxrwx for "."

When I go into one of the green-highlighted directories I have some files displayed in pink text (and some in normal white/grayish). What does pink mean? The pink and normal files have the same permissions on them so I can't tell what's different (all are -rw)

Sorry, is there a place where I can reference for all the colors I'm likely to come across at some point?

---

### Post by srs5694 on 2010-05-20
Don't get too hung up on the colors. They aren't standardized; Ubuntu might give different colors from Fedora, and both of those might be different from SUSE. Sometimes the colors reflect filename extensions (.jpg vs. .mp3 vs. .txt, for instance), and of course that's completely irrelevant for fixing the problem you've got.

When fixing permissions issues, pay attention to the permissions string and the ownership. Try Googling "Linux permissions" for some tutorials. That search turned up quite a few, but I didn't evaluate them all in detail, so I can't offer a specific recommendation.

---

### Post by BklynKid on 2010-05-20
I looked again and the pink files were indeed of the same extension.

Although the green highlight still confuses me a bit. Is there a file reference that might tell me what this is, inside my Ubuntu installation somewhere (since you said it's different from distro to distro)?

I appreciate the help, thank you.

---

