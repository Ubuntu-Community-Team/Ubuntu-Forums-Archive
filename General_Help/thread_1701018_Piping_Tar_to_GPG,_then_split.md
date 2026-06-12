---
title: "Piping Tar to GPG, then split"
date: 2011-03-05
forum: General Help
---

### Post by jbiggs12 on 2011-03-05
Hello,
I was wondering if it was possible to make my backup process a bit easier. I currently backup my system using three commands, one creating a tar backup of my computer, the next encrypting the file with GPG, and then the last one splitting the file into chunks of 512MB. I was hoping that this could be made a bit more simple by using pipes, something like
```
tar cpj / | gpg -c | split /media/Backup/$(uname -n).$(uname -r).$(date +%y-%m-%d).backup
```

But when I try it in the terminal I get really funky results. Any solution?

---

