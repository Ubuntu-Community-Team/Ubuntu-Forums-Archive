---
title: "Downloaded .pdf files in Chrome not temporary"
date: 2010-05-21
forum: General Help
---

### Post by donsy on 2010-05-21
I recently installed Chrome 5.0.375.53 beta from the Google Web site. I'm pretty much satisfied with its behavior except for one rather annoying quirk. When I click to view a .pdf document in Document Viewer the file is downloaded into my Downloads folder and then opened. That's fine. But the file remains there even after I remove all entries from the Download list and quit Chrome. I don't want my Downloads folder to fill up with a bunch of .pdf files that I view only once and never again. Is there a way around this? Firefox downloads the files into /tmp and deletes them automatically after I close the application. That's the way I expected Chrome to handle them also.

Yes I'm aware that I can choose the download location. My issue is with retaining those files after viewing them and closing Chrome.

---

### Post by Chesamo on 2010-05-21
Not with PDF files, no. It just downloads them and opens them as a standard file. You can try using the [Docs PDF/PowerPoint Viewer](https://chrome.google.com/extensions/detail/nnbmlagghjjcbdhgmkedmbmedengocbn) instead.

---

### Post by donsy on 2010-05-21
> **Chesamo said:**
> Not with PDF files, no. It just downloads them and opens them as a standard file. You can try using the [Docs PDF/PowerPoint Viewer](https://chrome.google.com/extensions/detail/nnbmlagghjjcbdhgmkedmbmedengocbn) instead.

Thanks for your reply. I installed Google's Docs PDF/PowerPoint Viewer but still get the same results. The file downloads and opens in Ubuntu's Document Viewer.

---

### Post by Chesamo on 2010-05-21
Chromium doesn't handle Opening files the same way Firefox does, so if you can't find an extension that mimics this behavior, then I don't think you'll get what you're looking for.

---

### Post by lovinglinux on 2010-05-21
You can install [gPDF](https://chrome.google.com/extensions/detail/egljjohbmnnpicoiddaapkpejfpnmmpe) extension. I use the Firefox version and it works like a charm. Unfortunately, I can't test the Chrome version to see if it behaves like you described, because Chrome is not allowing me to install extensions.

---

### Post by fragos on 2010-05-21
This Chrome extension should do the job for you, works great for me. 

[https://chrome.google.com/extensions/detail/nnbmlagghjjcbdhgmkedmbmedengocbn](https://chrome.google.com/extensions/detail/nnbmlagghjjcbdhgmkedmbmedengocbn)

PDF, PowerPoint and other MS docs quickly open in Google docs. You can download from there if you wish.

---

