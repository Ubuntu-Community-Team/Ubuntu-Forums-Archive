---
title: "GRUB_CMDLINE_LINUX_DEFAULT=&quot;profile&quot; option"
date: 2011-10-17
forum: General Help
---

### Post by rmlrml on 2011-10-17
so i've been looking at tips on improving boot speed, pages such as

[http://www.techtipsgeek.com/speed-up-boot-up-process-ubuntu-10-04-lucid-lynx/9496/](http://www.techtipsgeek.com/speed-up-boot-up-process-ubuntu-10-04-lucid-lynx/9496/)
and
[http://community.linuxmint.com/tutorial/view/114](http://community.linuxmint.com/tutorial/view/114)

the problem is they're about evenly divided in whether they advise you to leave the "profile" option in there, or to only boot with it once and then remove it.  any definitive answer?  thanks :)

---

### Post by ajgreeny on 2011-10-17
You should only use the profile boot option the one time.

It is much easier to do it on the fly from your grub menu.
If you don't usually see that hold shift at boot to make it appear, then hit "e" on the line you normally boot.  This will show you the full grub stanza for your kernel.  Usng the cursor keys go to the line that ends "quiet splash" and add the word profile ie "quiet splash profile".  Now hit Ctrl+X to boot and the profile option will run just the one time, as is should.  Next boot will be back to a normal default.

I haven't used this for some time, not at all in 10.04, if I remember correctly, but I don't think it made much difference the last time I did try it.  Have a go yourself, but don't allow the profile to run every time;  it slows boot time quite a lot, and that is what it is supposed to speed up.

---

### Post by rmlrml on 2011-10-17
thanks!

---

