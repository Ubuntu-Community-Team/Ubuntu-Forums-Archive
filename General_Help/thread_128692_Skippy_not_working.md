---
title: "Skippy not working"
date: 2006-02-12
forum: General Help
---

### Post by jdralphs on 2006-02-12
Hello -- I just installed Skippy from the universe repository and when i try to run it i get this result:

WARNING: Couldn't load config file '/home/jdralphs/.skippyrc'.
WARNING: $HOME/.skippyrc not found loading default config.
X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  33 (X_GrabKey)
  Serial number of failed request:  90
  Current serial number in output stream:  90

Anyone know how to fix this?

---

### Post by dcstar on 2006-02-12
[QUOTE=jdralphs]Hello -- I just installed Skippy from the universe repository and when i try to run it i get this result:

WARNING: Couldn't load config file '/home/jdralphs/.skippyrc'.
WARNING: $HOME/.skippyrc not found loading default config.
X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  33 (X_GrabKey)
  Serial number of failed request:  90
  Current serial number in output stream:  90

Anyone know how to fix this?[/QUOTE]
Does the man file say you have to copy over a sample .skippyrc file and modify it to your requirements?

---

### Post by krazykit on 2006-02-14
There's a file in the source tarball [on the homepage](http://thegraveyard.org/skippy.php) that has the default settings, but... I also get the "Bad Access" error

```
X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  33 (X_GrabKey)
  Serial number of failed request:  90
  Current serial number in output stream:  90
```
Which I still cannot figure out.

---

### Post by jdralphs on 2006-02-20
yeah.  the problem was that the default key is F11, I think for skippy and I'd already had that kep mapped to something else -- fixed now thank you!!

Though, I am having a problem with skippy duplicating the image for one window onto all other windows it displays.  Does anyone know what would cause it to do that?  I haven't surfed these forums yet -- If I find anything I'll link it here.

---

