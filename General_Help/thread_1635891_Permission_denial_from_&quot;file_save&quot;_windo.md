---
title: "Permission denial from &quot;file save&quot; window"
date: 2010-12-02
forum: General Help
---

### Post by maxxum on 2010-12-02
This is a recent issue that cropped up. I have been using this machine for a while and have done distribution upgrade twice. Now it runs 10.10 and 2.6.35-23-generic kernel.
I save all my data to a partition which is auto mounted on boot. I can create folders and move filed to it in nautilus. However when I want to save for example a PDF file from the internet and in the "Save" dialogbox of Firefox I want to save it (or create a new folder for it) it says "Error creating directory: Permission denied".
I did chown (which I should not have had to do as I can create directories in that partition if I go from file browser). The problem persists. 
I opened a PDF file from the internet and wanted to save a copy of it but it does not let me save from the document viewer as well.

Any help would be appreciated. Thanks!

EDIT: found the reason, it only does that when the filename does not have an extension (or a 'known' extension?). Still is there a way around this other than adding a known extension?

---

