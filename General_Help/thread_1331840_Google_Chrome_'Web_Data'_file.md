---
title: "Google Chrome 'Web Data' file?"
date: 2009-11-19
forum: General Help
---

### Post by jjsonp on 2009-11-19
I use Chrome on my Windows machine, and got it working fine on the latest 64-bit Ubuntu build.

I use Chrome's 'Search Engines' feature rather than bookmarks as they allow 'keywords' which I use constantly.

I discovered that under Windows I could copy the file from 'C:\Users\[username]\AppData\Local\Google\Chrome\User Data\Default\Web Data' to another machine with Chrome installed and all the 'Search Engine' customizations would transfer.

However I cannot find a synonymous file to overwrite on Ubuntu's Chrome install. (I searched the file system as su for "Web Data" - nothing). I found some Chrome files at opt->google->chrome, but that's it.

Thanks for any ideas. (Also I just noticed that when I try to select a 'prefix' for this all the options are blank - Chrome is in alpha;)

---

### Post by dmdil on 2009-11-19
i have same problem. can anyone tell the location of web data folder on ubuntu 9.10 for chrome!!!

thank

---

### Post by fragos on 2009-11-20
I run Chromium and it's "Web Data" file is in ~/.config/chromium/Default

---

### Post by jjsonp on 2009-11-21
Thanks fragos. However I don't seem to have that folder on my system (9.10 64-bit).

Someone pointed me toward the 'web-data' file at /etc/apparmor.d/abstractions, but that is a different file.

I'm guessing that Chrome under Ubuntu stores the Search Engine data in a different file or manner than under Windows.

---

### Post by sm94010 on 2009-12-09
```
~/.config/google-chrome/Default/Web Data

```
:)

---

### Post by jjsonp on 2009-12-09
Bingo - exactly what I was looking for! Thanks!

---

