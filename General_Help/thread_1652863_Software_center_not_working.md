---
title: "Software center not working?"
date: 2010-12-25
forum: General Help
---

### Post by Cheetah1933 on 2010-12-25
Everytime I try installing or uninstalling a program in the software center, it gives me this error

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 938, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

I am running 10.10, any suggestions?

---

### Post by andymorton on 2010-12-25
> **Cheetah1933 said:**
> Everytime I try installing or uninstalling a program in the software center, it gives me this error

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 938, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

I am running 10.10, any suggestions?

You could try the following - Go to the synaptic package manager, find the package in question. Click on edit and choose fix broken packages. I'm not guaranteeing it will work but it's worth a try.

andy:)

---

### Post by Cheetah1933 on 2010-12-25
Okay, I reinstalled the broken software (firefox in this case), but how do I run it if I don't have a shortcut to it? (I screwed it up somehow, but it's fixed now, and I have no shortcut to it.)

---

### Post by andymorton on 2010-12-25
Right-click on your gnome panel and choose ''add to panel''. Click on custom application launcher. Put Firefox in the name field and browse to where the programme is on your system to fill the command field. For me this is usr/lib/firefox. Click ok and you're done. 

andy

---

### Post by Cheetah1933 on 2010-12-25
I did that, but it takes me deeper into the firefox folder, and the only thing in there is a folder called "plugins". What am I doing wrong?

---

### Post by andymorton on 2010-12-26
> **Cheetah1933 said:**
> I did that, but it takes me deeper into the firefox folder, and the only thing in there is a folder called "plugins". What am I doing wrong?

In that case go to /usr/bin/firefox. Drag the icon to the panel and a screen will pop up asking you type in the name of the programme. When you've done that the launcher will be there.

andy

---

