---
title: "Adobe flash player won't install..."
date: 2010-07-16
forum: General Help
---

### Post by ChosenDev on 2010-07-16
I tried installing it with the .deb package and it said "Error: Wrong architecture 'i386'", and when I tried the .apt package it said "Error: Package `adobe-flashplugin` couldn't be found".

Any suggestions/ideas? I'm running it off a disk so that I can make sure it works.

---

### Post by mike555 on 2010-07-16
I'm not sure you can "install" flash when running off a live disc ........

---

### Post by snowpine on 2010-07-16
Welcome to the forums!

One of the big differences between Ubuntu and Windows is that we do not randomly download and install software from the internet (for example downloading Flash from the Adobe website). Rather, we use a tested and trusted "repository" of software provided by the Ubuntu developers.

Because Adobe only develops Flash for 32-bit architecture, you'll have to follow an extra step since you are running 64-bit. (At least, this is what I'm assuming based on the error message; correct me if I'm wrong!)

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

Notice the "ubuntu.com" in the URL that indicates you can trust these instructions to be Ubuntu-specific. ;)

Good luck! :)

---

