---
title: "Like encfs but with compression"
date: 2012-09-23
forum: General Help
---

### Post by vexorian on 2012-09-23
You know encfs, it basically allows you to create an encrypted folder. Which is mounted in another folder using a password. While you work in this other folder, it is the same as if it was any folder in your file system. Has file attributes, programs read and write to it just fine, etc. But in reality, the real folder is what is being worked with and with encryption.

I am trying to make a system to periodically backup my home using rsync. It works well, except that of course, rsync can't compress stuff, and I'd like to save space in my external drive. The optimal solution would be something like encfs, but with compression instead of encryption. So that to rsync, it is all the same, but the result is that the files with more redundant bits will not take too much space.

Does this thing like encfs but with compression instead of encryption exist?

---

