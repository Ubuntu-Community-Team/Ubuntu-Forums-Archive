---
title: "kinit is busted -- &quot;No resume image&quot;"
date: 2009-08-07
forum: General Help
---

### Post by edhawk2 on 2009-08-07
I'm using 8.01 on a Dell laptop (C620, PIII) which was working fine but now when I try to boot it gives me the following screen:

Loading, please wait
19+0 records in
19+0 records out(dev
kinit: name_to_dev_t(/dev/sda5) = dev(8,5)
kinit: trying to resume from dev/sda5
kinit: No resume image, doing normal boot

I am then left at a command line log in prompt.  

I'm not a programmer.  I don't know how to start the graphic interface.  

How can I get back into the system without destroying all of my recent work?

---

### Post by martinbaselier on 2009-08-07
The message is normal, you probably never paid attention to it before. startx will start x-org. Is gdm installed?

This will install it:
**sudo apt-get install gdm**

---

### Post by edhawk2 on 2009-08-07
I ran startx.  Here's what came of it:

startx
exec: /usr/bin/X11/X: not found, giving up
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3):Server error.

What does this mean?

---

### Post by tyrian on 2009-11-30
I am having the same problem edhawk.  Did you get it fixed?

---

