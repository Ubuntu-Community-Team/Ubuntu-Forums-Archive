---
title: "Software update error in 12.04"
date: 2012-04-29
forum: General Help
---

### Post by furmada on 2012-04-29
I have just upgraded to Ubuntu 12.04 on my Acer Aspire One.
Now, when I run sudo apt-get update, or click "Check" in Update manager, I get the following error:


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release](http://security.ubuntu.com/ubuntu/dists/precise-security/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

Is there anything I can do to fix this?
Thanks!

---

### Post by imachavel on 2012-04-29
have you tried going into the Bios and selecting 'fix broken packages' from the grub?

It's kind of like the equivalent of repair windows from the windows install disk, except way more reliable, and usually a much quicker processor, over all more efficient

[http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html)

may help you out a bit. It isn't completely on the same level as an error occurring AFTER the OS and gui load, but the concept is the same, and basically you need to fix a change in the kernel which has caused your updates to fail. Read it carefully, and if your answer isn't there, google for an answer to how an upgrade can cause a fail in updates because of kernel changes

---

