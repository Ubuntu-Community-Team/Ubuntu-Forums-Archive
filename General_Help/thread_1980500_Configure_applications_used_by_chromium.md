---
title: "Configure applications used by chromium"
date: 2012-05-15
forum: General Help
---

### Post by chromatine on 2012-05-15
Hello,

I hope this is the relevant forum for this question, please redirect me if this is not the case.

I'm currently trying out chromium and I'd like to configure which applications it uses to open files. After some web research I fount it's supposed to use xdg-open. The problem is in my case it does not seem to use xdg-open at all.

If I run 
$ xdg-open some-pdf-file
from a terminal the file is opened with evince.
If I click on a pdf file in a web page I get a prompt for where to download the file.

I tried removing xdg-open and replacing it with a symlink to mimeopen (which opens pdf files with xpdf), and still get the same result.

I feel like I'm missing something, but have no idea what.

---

### Post by Zvlwab on 2012-05-15
When downloading a file, click on the arrow next to it and click "Always Open Files of This Type"

---

### Post by chromatine on 2012-05-15
Aaaah! :)

That did the trick perfectly thanks! :)

---

