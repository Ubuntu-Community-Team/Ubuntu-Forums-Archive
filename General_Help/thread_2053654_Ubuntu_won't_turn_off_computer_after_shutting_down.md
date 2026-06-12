---
title: "Ubuntu won't turn off computer after shutting down"
date: 2012-09-05
forum: General Help
---

### Post by Hekabe on 2012-09-05
Ubuntu doesn't turn off my computer after it shuts down. All the normal shutdown dialogs come up and then the screen goes black, but it stays powered on.
I have a Dell Latitude D630. I use it with a dock most of the time, but I tried it off the dock and got the same result.
Any help?

---

### Post by angry_johnnie on 2012-09-05
Not entirely sure this will work with grub2 but worth a try:

press alt + f2 and type

```
gksu gedit /etc/default/grub
```

it will open a text file.

look for **GRUB_CMDLINE_LINUX_DEFAULT=" "**

after the = sign it may say something like **"quiet splash"**

add **"acpi=force"** minus the quotes

so it should be something like this:

**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"**

Save and close the file.

Then open a terminal and type:

```
sudo update-grub
```

Press enter and type in  your password.

Reboot, and try to shut down.

I had to do that with an older computer I had, but that was with ubuntu 7.04 and legacy grub.  It may still work, though.

---

### Post by Hekabe on 2012-09-09
That worked. Thanks a lot.

---

