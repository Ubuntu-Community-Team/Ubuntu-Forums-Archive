---
title: "Rar file not extracting"
date: 2010-06-27
forum: General Help
---

### Post by Nater43 on 2010-06-27
When I try to extract a rar file with either the default package manager or Ark, it always results in a correctly named folder being created, but the files themselves are never extracted. Why is this? How can it be fixed?

---

### Post by Spr0k3t on 2010-06-27
It's possible you don't have rar installed.  Check that by typing unrar in the terminal.

---

### Post by Nater43 on 2010-06-27
I just double checked, and I do have unrar installed. I ran it on a .rar file, in terminal, and it said failed next to all of the files. They failed to extract.

---

### Post by AlexDudko on 2010-06-27
Are there any mistakes? Can it be that the files are corrupted?

---

### Post by Barafu Albino Cheetah on 2010-06-27
If I recall it right, once upon a time there was a buggy version of unrar that needed write permissions to read the file.

---

### Post by Nater43 on 2010-06-27
> **AlexDudko said:**
> Are there any mistakes? Can it be that the files are corrupted?

Its possible, but highly unlikely. This has happened with multiple different .rar packages. Conversely, .zip packages work fine.

---

### Post by Nater43 on 2010-06-27
Bump

---

### Post by Rhubarb on 2010-06-27
Try installing **p7zip-rar** then use the default ubuntu archive manager (file-roller) to extract it.
Hopefully it'll work for you :)

---

### Post by AlexDudko on 2010-06-27
I can't reproduce it on my computer, so I can't give you any advice.

---

### Post by mister_playboy on 2010-09-06
I never had this issue with file-roller on 9.04, but I see it quite a bit with Ark on 10.04.  My workaround is to extract these troublesome .rars with 7z from the command line.  That always seems to work.

---

### Post by AlexOnVinyl on 2011-09-19
I too am having this problem. I will try the p7zip

---

### Post by sisco311 on 2011-09-19
Please don't bump old thread and don't cross post.

Thread closed.

---

