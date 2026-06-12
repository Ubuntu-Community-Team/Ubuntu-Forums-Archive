---
title: "Press S to skip mount or M for manual recovery."
date: 2010-10-30
forum: General Help
---

### Post by iampriteshdesai on 2010-10-30
I have installed Ubuntu 10.10 x64 bit edition. On booting Ubuntu wouldn't mount my partitions, so I installed pysdm to auto mount them during booting. But since then I often get during boot: Press S to skip mount or M for manual recovery.

What should I do?

---

### Post by Mangrove on 2010-11-02
I had this problem when I upgraded from 9.x to 10.4. It has something to do with /etc/fstab trying to mount a drive/media/usb that is not there.

When you get to that "press s to skip" screen, press the "esc" key and note the last line. Then press "s" and it will quickly flash "skipping ..." (in my case it was skipping mounting the USB dev for Virtualbox that I no longer had installed).

Now open a terminal and type:

sudo gedit /etc/fstab

Now comment out the line that it is skipping by putting a "# " (pound sign and a space) in front of that line. The line it skipped should be right after the last line noted above.

I found out how to do this from similar problems people reported to launchpad.

Hope this helps!

---

### Post by fayeav on 2011-12-25
Thanks very much for the reply to that error! I am trying to find a solution for two days now! :-)

---

