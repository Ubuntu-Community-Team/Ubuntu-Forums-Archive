---
title: "Need help with ttf-mscorefonts-installer package"
date: 2011-10-14
forum: General Help
---

### Post by KuroiClover on 2011-10-14
I am having trouble with the ttf-mscorefonts-installer package.  When I try to delete it, I get an error saying I do not have permission to delete it.
When I try to reinstall it, I'm getting this message:

"An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Details:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package."

Can I get some help with this?  I was getting the same message while trying to get Flash to run (I just upgraded to 11.10), but luckily that worked after a restart.

---

### Post by thatguruguy on 2011-10-14
you might try the following in a terminal:
```
sudo apt-get -f install
```

---

### Post by KuroiClover on 2011-10-14
I did that, and it brought me to this ([http://www.microsoft.com/typography/fontpack/eula.htm](http://www.microsoft.com/typography/fontpack/eula.htm)), but in the terminal, with the same link to that page.  I'm not exactly sure where to go from there.
Attached is a screenshot of what I see in the terminal.

---

### Post by sikander3786 on 2011-10-14
Click anywhere inside you Terminal to focus it. Then press <Tab> and <Enter>. Repeat if another dialog appears.

---

### Post by KuroiClover on 2011-10-14
Thanks so much!
Everything works just fine now.  I'll go mark this as solved.
Thanks again.

---

