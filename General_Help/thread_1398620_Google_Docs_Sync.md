---
title: "Google Docs Sync"
date: 2010-02-04
forum: General Help
---

### Post by moulari on 2010-02-04
Since Google now offers storage for every file type in gDocs does anyone know of a simple sync solution, something like dropbox for Google Docs? 

I tried conduit, but no luck. I tried some of the python tools for import and export but they don't really fulfill my needs.

thanks for all suggestions

---

### Post by korami on 2010-04-28
This is something I am interested in too.

Google Docs has now really great storage plans, however without a 2-way backup solution they're almost useless.

---

### Post by megamania on 2010-04-29
[http://code.google.com/p/google-docs-fs/](http://code.google.com/p/google-docs-fs/)

you mount your google docs account as a file system, then you can rsync etc.

---

### Post by korami on 2010-04-29
> **megamania said:**
> [http://code.google.com/p/google-docs-fs/](http://code.google.com/p/google-docs-fs/)

you mount your google docs account as a file system, then you can rsync etc.

Thanks, I will try it out.

---

### Post by tekhawk on 2010-04-30
Has anyone had any luck with Google-Docs-FS on Lucid? I have not used Python much so not sure not sure where to start with the Python errors I keep getting

---

### Post by tekhawk on 2010-04-30
Here is the error I keep getting

[PHP]  File "/usr/lib/python2.6/dist-packages/google-docs-fs/gFile.py", line 28, in <module>
    import gNet
  File "/usr/lib/python2.6/dist-packages/google-docs-fs/gNet.py", line 22, in <module>
    import gdata.docs.service
ImportError: No module named gdata.docs.service
[/PHP]

---

### Post by jandrusk on 2010-08-27
I got it to work on Lucid, but even on my broadband cable modem, the response was horrible. I think it took like 10 - 15 minutes before the ls listing would complete.

---

