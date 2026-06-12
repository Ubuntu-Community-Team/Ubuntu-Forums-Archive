---
title: "new ubuntu user help"
date: 2010-11-08
forum: General Help
---

### Post by alhaji on 2010-11-08
sorry if this is the wrong section, i have no idea. :(
ok, i just downloaded ubuntu 10.10, the 'windows installer' way.
[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)
i finished everything and then went into the boot manager and choose to start up ubuntu, it started and went to a purpleish screen then it started to have some installation thing, i was watching the whole time, and throughout the installation it asked to 'skip' a part, i thought it would do no harm though... and i don't know if it did.
well after the installation it sent me back to the boot manager, i tried running ubuntu again, but it would just send me back to the boot manager...

tl;dr:
i downloaded ubuntu the windows installer way, i let it install, but when it asked me to skip a part i did skip it.
now i cannot open up ubuntu, it keeps sending me back to the boot menu thingy.

is there anyway to fix this? or is there a way to uninstall it?

i am currently using windows 7.

---

### Post by Jetso on 2010-11-08
After the Ubuntu logo, what happened again, I'm having trouble understanding what you said :( . By Windows Installer do you mean Wubi? Can you repeat this process?

---

### Post by alhaji on 2010-11-08
> **Jetso said:**
> After the Ubuntu logo, what happened again, I'm having trouble understanding what you said :( . By Windows Installer do you mean Wubi? Can you repeat this process?

[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)
i did it under that process, i followed the instructions and all on the page.

the problem is, after the main installation process, it just went to the boot manager (there's a picture of it on the link i posted)
and it keeps sending me back after i select 'ubuntu' there.

---

### Post by bcbc on 2010-11-09
Don't skip any part of the install. If you skip it doesn't install lupin which is required to boot a wubi install. [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/620028](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/620028)

---

### Post by Jetso on 2010-11-10
The way you installed is called "Wubi."

I just suggest you don't skip anything!

---

### Post by SINNISTER on 2010-11-10
I'd recommend just Downloasding 10.04 LTS in an .ISO format write it to CD and then Install it that way.

Quiet simple to do, you can even test it out as a live disc before making a final decision on installing it....

Enjoy Ubuntu, its awesome and dont be afraid to post any problems on the Forum, we all started somewhere :) so we understand where you coming from..... Ask me I know.. hahaha

---

### Post by Jetso on 2010-11-10
I do suggest what SINNISTER said, but beware it does have risks, although it leads to a better Ubuntu/Linux experience. To do this you will have to shrink your Windows partition, then make a / partition and a swap (2.5x of your RAM) partition and you'll be good, but there are better guides on here than what I'm telling you :p

---

