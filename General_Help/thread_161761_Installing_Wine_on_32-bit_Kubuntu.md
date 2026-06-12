---
title: "Installing Wine on 32-bit Kubuntu?"
date: 2006-04-17
forum: General Help
---

### Post by Rakanishu on 2006-04-17
Hi.
I have been trying to install wine on my 32-bit Kubuntu dist.
I have followed this little guide: [http://ubuntuforums.org/showpost.php?p=898111&postcount=2](http://ubuntuforums.org/showpost.php?p=898111&postcount=2).
But when I enter 'sudo apt-get update' I get the reply that the: 'Line 1 in /etc/apt/sources.list has the wrong format (dist)'.
What does this mean, and what should I do now?

Thanks in advance

---

### Post by Ensnared on 2006-04-17
Well, it's just a wild guess, but it might mean that there's something wrong with the first line in your /etc/apt/sources.list. What does that line look like?

---

### Post by Rakanishu on 2006-04-17
Hi, thanks for the answer.
It says:
deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/

---

### Post by Ensnared on 2006-04-17
Strange, nothing wrong with that line. It does point to the CD though, so you might as well comment it out (e.g. add a # in front of it) since you'll likely be wanting to download any packages you're going to install instead to get the latest version.

It might be that the error happens if the Kubuntu CD isn't inserted into your drive, but I've never tried since commenting out that line is one of the first things I do after performing a fresh install.

---

### Post by Rakanishu on 2006-04-17
I commented the two first lines, and everything worked fine. 
Thanks!

---

