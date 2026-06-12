---
title: "'net usershare' returned error 255"
date: 2012-08-12
forum: General Help
---

### Post by MrsUser on 2012-08-12
I got this error today when I simply looked up the properties of an external hard disk. I assume it's a bug. But forum entries etc date back to 2010, so I don't know how much this is related to my problem in Ubuntu 12.04 (64-bit) and how to fix it. Any help is appreciated, because this error keeps coming back with the dialog window and the properties dialog locked up.

[IMG]http://i.imgur.com/H6K9V.png[/IMG]

There was an error while getting the sharing information

'net usershare' returned error 255: net usershare: cannot open usershare  directory /var/lib/samba/usershares.
Error No such file or directory Please ask your system administrator to enable user sharing.

---

### Post by sanderj on 2012-08-12
If you post the text in the popup windows as text (and not as a picture), it makes indexing it possible.

And ... does /var/lib/samba/usershares exist? Probably not.

---

### Post by MrsUser on 2012-08-12
No, that folder doesn't exist. Perhaps I should create it?

---

### Post by Morbius1 on 2012-08-12
It sounds like you have a package missing:
```
sudo apt-get install nautilus-share
```

---

### Post by MrsUser on 2012-08-12
nautilus-share is installed. I just checked with synaptic.

However, I created this directory now. Let's see what happens. The problem occurs randomly. Sometimes this error comes up, sometimes not. Could it be that it has something to do with NTFS formatted hard  disks? Because the folder I wanted to check was on an external, NTFS formatted drive.

---

### Post by MrsUser on 2012-08-25
After I've created that directory, the error didn't come up again. Seems to be fixed that way.

---

