---
title: "Mount Problem"
date: 2006-05-12
forum: General Help
---

### Post by cssutto on 2006-05-12
Last night, in trying to get VLC to play properly, I had it lock up and nothing I knew how to do would close it properly.

So I shut Ubuntu down using sudo shutdown -h now.

This morning I wanted to look at some files on my external Maxtor and when I tried, using applications accessories file browser, I got the following error message:

Error: directory /media/usbdisk is not empty
Error: could not execute pmount

Looking at this file with file browser, it says that it is empty.

How do I get rid of this problem?

CSSJR

---

### Post by louis_nichols on 2006-05-12
well... something happened there. try to delete and re-create the folder (MAKE SURE IT'S NOT MOUNTED, FIRST! OR YOU'LL BE DELETING YOUR OWN FILES):

sudo rm -rf /media/usbdisk && sudo mkdir /media/usbdisk

Then try to remount it:

sudo mount -a

---

### Post by cssutto on 2006-05-12
Beautiful.

You know what you are doing.

Worked like a charm.

Thank you.

CSSJR

---

