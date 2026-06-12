---
title: "Where are the packages downloaded?"
date: 2011-11-27
forum: General Help
---

### Post by rva1945 on 2011-11-27
I need to install packages in the notebook, which for unknown reasons detects the wireless network but refuses to connect. So I want to download a wireless manager and copy it to a pendrive and then install it into the notebook. How do I download a package (without installing it automatically, I mean, I need to copy it to another computer?.

Thanks

---

### Post by 001neeraj on 2011-11-27
You can can copy the entire .deb packages from the directory "/var/cache/apt/archives".
You have to exclude the file "lock" in the same folder. Because, you can't copy the packages when you include "lock".

---

