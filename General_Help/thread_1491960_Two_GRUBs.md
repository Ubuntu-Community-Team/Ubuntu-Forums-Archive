---
title: "Two GRUBs"
date: 2010-05-24
forum: General Help
---

### Post by The Switch Blade on 2010-05-24
I installed ubuntu from within Windows 7, but it didn't work, so I reinstalled it from the disc.

Now when I turn on my computer, it goes to Grub, where I have the choice of ubuntu, memtest, and win7, and if I select win7, then I again go into Grub and get to choose from win7 and ubuntu.

Any way to remedy this?

---

### Post by WorMzy on 2010-05-24
That shouldn't happen. I can't even think anything that would cause that behaviour. Are you sure it's a different grub, not the same one?

If you have multiple hard drives, try reordering the boot order of them in the bios.

---

### Post by WorMzy on 2010-05-24
Actually, I just thought of something that would cause grub to display this behaviour, but I don't know how to remedy it in grub2. In grub legacy, you can make it "chainload", thereby handing control over to a different bootsector with the 'chainloader +1' option. I get the feeling that this is what is happening here, grub is incorrectly chainloading another version of grub, instead of the Windows bootsector.

Like I said, I don't know how to fix this in grub2. Have a look at some other posts relating to grub2, or wait for someone else to explain what files you need to change.

---

### Post by oldfred on 2010-05-24
You have a wubi install that is the second menu. You have to uninstall the wubi in windows. I do not have win7 but if the uninstall does not remove the wubi entry then I think you use bcdedit.

More instructions:
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

---

### Post by The Switch Blade on 2010-05-26
I know. The problem is that I deleted the partition where I installed wubi. So I can't uninstall it.

---

