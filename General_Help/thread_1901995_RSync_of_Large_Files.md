---
title: "RSync of Large Files"
date: 2011-12-29
forum: General Help
---

### Post by IMSargon on 2011-12-29
FILE is a virtual machine disk at 50GB. It exists on the local hard drive (/LOCAL/FILE) and a USB external drive (/REMOTE/FILE). In my test, FILE is identical in both places. Then I boot up the /LOCAL/FILE virtual machine, create a text file on the desktop, then shut down again. My goal is to synchronize this seemingly minor change in a reasonable amount of time.

Here's what I've tried:
rsync --progress -c --inplace --no-W /LOCAL/FILE /REMOTE/FILE
rsync --progress --inplace --no-W /LOCAL/FILE /REMOTE/FILE
rsync --progress /LOCAL/FILE /REMOTE/FILE

In each minor change case, RSync transfers the full 50GB. Is there anything else I can tweak? If the files are already identical, RSync behaves as expected, and does not transfer 50GB.

---

### Post by papibe on 2011-12-30
Hi IMSargon

Are either /LOCAL or /REMOTE NTFS? If so, you may need to take a look at the --modify-window option.

If not, I think this is what is happening: in order for rsync to update the file it has to take the source, read all blocks, checksum them, and then compare them with the destination.

When you use the option --progress, it may look like rsync is copying everything, but if you take a closer look, you'll notice that the transfer speed will be MUCH greater than the hardware limit (since it is not actually copying the blocks that are identical).

I hope that helps,
Regards.

---

