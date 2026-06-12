---
title: "Firefox 4 strange PNG colors since 11.04"
date: 2011-05-02
forum: General Help
---

### Post by Flaxis on 2011-05-02
Hello.

I upgraded to Ubuntu to 11.04, but when I now open firefox and go to localhost, some PNG images have really strange colors. This is not the case when I display the webpage in Google Chrome.
I'm not sure if I will have similar problems with all PNG's, but I wouldn't be surprised.

For instance, a random PNG in Firefox 4:
[IMG]http://dl.dropbox.com/u/6073499/screenshots/firefoxpng/firefox.png[/IMG]

And the **same** image in Chrome:
[IMG]http://dl.dropbox.com/u/6073499/screenshots/firefoxpng/chrome.png[/IMG]

What could be the problem? How do I solve this?

This only seems to hapen with alpha transparent images!

---

### Post by lovinglinux on 2011-05-02
See explanation and solution at [http://www.webgapps.org/firefox/issues-and-solutions](http://www.webgapps.org/firefox/issues-and-solutions)

Look for "Some images are displayed with weird colors" in the Rendering section.

---

### Post by Flaxis on 2011-05-02
It worked!
However, the value I had to enter for this 'key' was not 2 (this value was already assigned), but 3.
Thanks for helping me out!

---

### Post by lovinglinux on 2011-05-02
> **Flaxis said:**
> It worked!
However, the value I had to enter for this 'key' was not 2 (this value was already assigned), but 3.
Thanks for helping me out!

You are welcome.

---

