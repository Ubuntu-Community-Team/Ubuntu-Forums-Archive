---
title: "System Won't Boot. Again!"
date: 2009-12-28
forum: General Help
---

### Post by klausner on 2009-12-28
For the third time in as many weeks my system running 9.10 karmic wont boot. It starts, then dumps into a shell. Trying the recovery console doesn't work either. The errors are:

[INDENT]init: hwclock main process (nnn) terminated with status 2
.: can't open /etc/default/rcS
init: mountall main process (nnn) terminated with status 2
filesystem check failed[/INDENT]

Ran fsck manually from the shell prompt and from the Live CD, found some timestamp errors, fixed them, nothing else.

There are a [couple]("https://bugs.launchpad.net/ubuntu/karmic/+source/udev/+bug/432155") of [bugs]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/436076") open for clock update problems back in September, but they look like they were fixed.

dmesg output attached.

I'm tired of reinstalling Ubuntu! Is there a fix/workaround for this?

---

### Post by klausner on 2009-12-30
Bump! I'd really appreciate some suggestions to get this fixed.

---

### Post by john newbuntu on 2009-12-31
Do you have the file /etc/default/rcS that is owned by root and with read permissions?
Was any change made to the /etc directory?

---

### Post by klausner on 2009-12-31
> **john newbuntu said:**
> Do you have the file /etc/default/rcS that is owned by root and with read permissions?
Was any change made to the /etc directory?

There is no file /etc/default/rcS. I made no intentional changes in /etc.

---

### Post by john newbuntu on 2009-12-31
Can you type "init 2" or "sudo init 2" to see if anything good happens?

---

### Post by klausner on 2009-12-31
> **john newbuntu said:**
> Can you type "init 2" or "sudo init 2" to see if anything good happens?

No, nothing good happened :( 

Finally figured out that the error message was telling me something. THERE WAS NO /ETC/DEFAULT/RCS FILE!!! Why didn't someone here tell me I am an idiot and point this out! Copied the file from the CD.

Anyway, now X and Gnome start to boot, then I get 
> There is a problem with the configuration server
(/usr/lib/libconf2/gconf-sanity-check-2 exited with status 256

and I get a bare X environment, with no window manager. Tried several suggestions with file permissions found here, but no joy. So I'll close this thread, and start another one. :(

---

