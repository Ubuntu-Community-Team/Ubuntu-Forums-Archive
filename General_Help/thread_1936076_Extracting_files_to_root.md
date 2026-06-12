---
title: "Extracting files to root?"
date: 2012-03-05
forum: General Help
---

### Post by Sophin87 on 2012-03-05
Hi all,

I'm trying to install a dual boot of Win7 on my laptop and I'm kind of stuck on the details.
I'm following this guide: [http://ubuntuguide.net/how-to-install-windows-7-from-ubuntu-without-burnning-a-disc](http://ubuntuguide.net/how-to-install-windows-7-from-ubuntu-without-burnning-a-disc)

Most of the steps sound fairly straightforward, but I'm actually stumped on step one, extracting Grub to /. As far as I'm aware / is the File System folder, but I'm not allowed to alter anything in there.
Am I actually looking in the wrong place? If not, how do I extract those files?

Cheers in advance!

---

### Post by snowpine on 2012-03-05
The guide in your link is not written for a beginner and assumes intermediate-level knowledge. It skips over several steps that are not immediately obvious unless you've done them before. Furthermore it is written for an obsolete Ubuntu release. In other words, don't trust that site. :)

I think this is a better guide to dual booting Ubuntu/Windows: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Sophin87 on 2012-03-05
Thanks snowpine, I'll try that guide later tonight.

I'll update you on the progress.

---

### Post by snowpine on 2012-03-05
To answer the question posed in your thread title: 

To access files/folders outside of your /home folder, you need to use "sudo" ("gksu" for GUI apps) as described here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

For example you can extract to your /home folder, and then open your file manager with gksu to copy the files from your /home to / (root folder):

```
gksu nautilus
```

---

