---
title: "Shutter's web capture is not working"
date: 2011-06-02
forum: General Help
---

### Post by ubuntu27 on 2011-06-02
Hello everyone. I have been trying to use the web capture feature by Shutter. But, it always throws the same error message.

```
Error while taking the screenshot.
Unable to capture website

Usage: gnome-web-photo [--mode=photo|thumbnail|print]
[...]
Usage: gnome-web-photo [-c CSSFILE][-t TIMEOUT][-force][-w WIDTH][--file]URI|FILE OUTFILE
Unknown option--format=png
```

Thinking that perhaps it is an a bug with png files. I changed it to store the image as jpeg, and bmp as well. Those provided the same error except that it says jpeg or bmp instead of png.

Here is a screenshot:
[[IMG]http://img191.imageshack.us/img191/8321/screenshotshuttererror.th.png[/IMG]](http://img191.imageshack.us/i/screenshotshuttererror.png/)

Do you have any idea why this is happening? How can we fix it?


Shutter: 0.87.2
OS: Ubuntu Natty 64-bit
Desktop Environment: Gnome 2.32.1 with classic shell.

---

### Post by ranjank on 2011-06-04
I am suffering from same problem. I tried by reinstalling also. No use. I think its a bug.

---

### Post by ubuntu27 on 2011-06-05
It is a bug. They already fixed it in Shutter's daily build, which means that the fix will be available for the next version. :)

Bug Report:

[Bug #785608]("https://bugs.launchpad.net/ubuntu/+source/shutter/+bug/785608")
[Bug #791945]("https://bugs.launchpad.net/shutter/+bug/791945")
[Bug #77925]("https://bugs.launchpad.net/shutter/+bug/779252")

Can't wait for the update ^_^

---

### Post by simptechmike on 2011-10-02
Yes, the daily does seem to fix the issue :)

---

