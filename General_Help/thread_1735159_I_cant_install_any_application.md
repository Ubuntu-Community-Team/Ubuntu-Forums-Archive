---
title: "I cant install any application"
date: 2011-04-21
forum: General Help
---

### Post by tunechi on 2011-04-21
hi , i was installing last night some applications , then i forgot to  plugin my laptop so suddenly it turned off , anyways today i turned it  on , i am trying  to download some new application , but here is what i get 
" "Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 936, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the libsdl-perl package. This might mean you need to manually fix this package."

i reported the bug but didnt get a reply , hope some one here can help me , thank you

---

### Post by spikoley on 2011-04-21
I am not exactly sure whats going on, but here are some trouble shooting steps you can try.

```
sudo apt-get install -f
```

If that doesn't work then try installing libsdl-perl.

```
sudo apt-get intall libsdl-perl
```

---

### Post by Bernabé on 2011-04-21
That can be because the application you were installing did not finished to install, and some packages are missing or broken.
To fix that you can reinstall the application with the option --fix-missing, or -f, as spikoley said.
```
apt-get install <package> --fix-missing
```

---

### Post by Sidewinder1 on 2011-04-21
Ahem, wouldn't that be:```
sudo apt-get install <package> --fix-missing
```

I'm really big on "copy-paste" when it comes to command-line, in order to avoid syntax, punctuation, and space errors.
Not to nit-pick...:D:D

Side

---

### Post by dino99 on 2011-04-21
into synaptic: remove/purge then reinstall the broken app/package

---

### Post by tunechi on 2011-04-21
> **spikoley said:**
> I am not exactly sure whats going on, but here are some trouble shooting steps you can try.

```
sudo apt-get install -f
```If that doesn't work then try installing libsdl-perl.

```
sudo apt-get intall libsdl-perl
```
there first code work , thank you very much <3

---

### Post by spikoley on 2011-04-21
I am glad it worked.  To help others in the future mark this thread as solved.  Go to Thread Tools and mark as Solved.

---

