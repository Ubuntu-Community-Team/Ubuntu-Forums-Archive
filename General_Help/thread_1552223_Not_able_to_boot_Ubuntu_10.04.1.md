---
title: "Not able to boot Ubuntu 10.04.1"
date: 2010-08-13
forum: General Help
---

### Post by Abhinavhardikar on 2010-08-13
I recently did an MBR fix but now ubuntu boot stops here:

[http://i35.tinypic.com/jtb1hu.jpg](http://i35.tinypic.com/jtb1hu.jpg)

I tried to clean the voulume using fsck but no use!

Help me please

Thank you
Abhinav:)

---

### Post by dtfinch on 2010-08-13
I'd try setting your clock to 2010 in the bios. I'm surprised that it'd refuse to boot because of that, but after searching around, it looks like that's really how it's set up.

[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/510403](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/510403)

They mention a fix to /etc/e2fsck.conf to disable the error if fixing your time isn't enough.

---

### Post by Abhinavhardikar on 2010-08-13
OK the date thing worked but it still won't go ahead! I get this thing:

[http://i35.tinypic.com/t0hxtz.jpg](http://i35.tinypic.com/t0hxtz.jpg)

---

### Post by ASchweitzer on 2010-08-13
How long have you left it sit there? I had a ureadahead error a while ago and it went away after 10 minutes or so and booted...

Don't have any advice on the mountall failed though

---

### Post by Abhinavhardikar on 2010-08-13
left it for half an hour but nothing happened! :(

---

### Post by ASchweitzer on 2010-08-13
Have you tried google for that error? I'm of no more help unfortunately.

---

