---
title: "what does this command do and why do i need to run it in order to get minecraft torun"
date: 2012-07-28
forum: General Help
---

### Post by vexaxv on 2012-07-28
i had an issue with minecraft giving me a black screen everytime i tryed to play with openjdk7 so i found this command to run..

export LD_LIBRARY_PATH="/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/amd64"

then it fixed the issue, i wanted to know what this command does and why did i need to run it so if i ever have an issue like this again ill know more about why and how. thank you

---

### Post by NilPointer on 2012-07-28
This command sets environment variable, which tells programs where to look for shared libraries. Apparently openjdk7 needs some library to start up properly, which is stored at that path. Or maybe it needs amd64 version.

---

