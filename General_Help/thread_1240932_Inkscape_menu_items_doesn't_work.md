---
title: "Inkscape menu items doesn't work"
date: 2009-08-15
forum: General Help
---

### Post by user34532 on 2009-08-15
Ubuntu is 9.04 x86_64.
Installed Inkscape 0.46 through:
```
sudo apt-get install inkscape
```Getting error when clicking Inkscape's Help menu items through "Inkscape Manual" to "SVG 1.1 Specification"

```
Inkscape has received additional data from the script executed.  The script did not return an error, but this may indicate the results will not be as expected.

(gnome-open:15292): GLib-CRITICAL **: g_path_get_basename: assertion `file_name != NULL' failed
Error showing url: Failed to execute child process "http://inkscape.org/doc/keys046.html" (No such file or directory)
```

---

### Post by SoftwareExplorer on 2009-08-16
Does anything under the tutorials work? It sound like it is not opening web pages correctly or something and the tutorial wouldn't be a web page, so it's a good test.

---

### Post by user34532 on 2009-08-16
All tutorials items works, only those help menu options with link to web doesn't work

---

### Post by SoftwareExplorer on 2009-08-16
Sounds like a web page issue then. Are you using the default browser? (Firefox) Does firefox work?
Edit:It looks like the error message tells you where it intended to go. Of course, it would just be better to fix it. So, I have your problem narrowed down, now we just need an expert to fix it.

---

