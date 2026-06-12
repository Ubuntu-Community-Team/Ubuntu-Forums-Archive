---
title: "Running a script from a USB drive"
date: 2010-01-11
forum: General Help
---

### Post by ohadle on 2010-01-11
Hi,

I'm trying to install a program from a CD ISO I have, using an install script on the ISO.
I tried to mount the ISO on my desktop and run the script from there, but doing "sudo ./installer" would just give me "command not found".
(The file was there)
I gave up and burnt a CD, ran fine from there.

But now I need to install this on a netbook with no CD drive! Only the USB to rely on.

Any ideas on how to run the script?

---

### Post by michy99 on 2010-01-11
1) Is the script executable?
2) When your run```
sudo ./installer
```are you in the directory that contains 'installer'? 

Sorry if these seem like dumb questions, but people often make these errors.

---

### Post by ohadle on 2010-01-12
Thanks for the reply:

I run the script in much the same way when I burn it to the CD, so:

1. Yes.

2. Yes. If I press "tab" it auto-completes the name.
Note that I mount the ISO file, so I am in something like /home/.gvfs/filename.iso/.

---

