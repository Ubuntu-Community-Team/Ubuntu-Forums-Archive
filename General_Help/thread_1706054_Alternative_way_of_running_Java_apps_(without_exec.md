---
title: "Alternative way of running Java apps (without executable bit)"
date: 2011-03-13
forum: General Help
---

### Post by Nohajc on 2011-03-13
Let me share this great finding with you:
I was trying to run .jar from fat32 flashdrive (simply by double-clicking) and it didn't work because of the lack of executable bit. And as we know, on fat32 you cannot set this permission.

But, there is a quick fix actually:
I just selected *open with another app *and then I chose my own command like this:
*"java -jar"*.
If you set this option to be remembered for this type of file, it will launch any .jar (again with a simple double-click) and it doesn't even require the file to be executable.

---

