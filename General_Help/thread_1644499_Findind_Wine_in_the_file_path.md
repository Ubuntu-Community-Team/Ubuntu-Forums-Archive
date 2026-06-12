---
title: "Findind Wine in the file path"
date: 2010-12-13
forum: General Help
---

### Post by Garrett85 on 2010-12-13
I'M trying to download crossover games but it wants me to choose an application to open the file with. I'M guessing I should point it toward wine. But when I search for wine in nautilus, I find way to many files and folders to choose from. I find the Linux filing system very confusing. Please help, thanks.

---

### Post by mendhak on 2010-12-13
Hi, go to your home directory in Nautilus, press Ctrl+H.  This shows you hidden folders.  You should find a .wine folder in there.  Have a look through that .wine folder for your application.

---

### Post by thameera on 2010-12-13
What's the type of file you're trying to open? If it's a tar.gz file you may need to extract it first.
If it needs to be opened with wine, go to a terminal and type
```
wine *filename*
```

---

