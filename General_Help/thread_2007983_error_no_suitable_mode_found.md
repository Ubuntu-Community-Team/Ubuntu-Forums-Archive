---
title: "error: no suitable mode found"
date: 2012-06-21
forum: General Help
---

### Post by decomp on 2012-06-21
Hello!

I am experiencing the following error at startup.

```
error: font format error: can't read section name
error: no suitable mode found.
error: cannot read the linux header.
error: you need to load the kernel first.

Press any key to continue...

   Failed to booth both defaults and fallback entries.

Press any key to continue...
```

Then I am taken to the grub menu and allowed to choose an older kernel, which works fine.

For a week or two it was just: 

```
error: font format error: can't read section name
error: no suitable mode found.
```

Then i ran update and it downloaded the new kernel 3.2.0-25 and the rest of the error began.

I have tried reinstalling anything grub related and the most recently downloaded kernel (3.2.0-25)

I googled around, but everyone else "solved" this by reinstalling. 

Anyone have any ideas?

---

### Post by decomp on 2012-06-23
:popcorn:

---

### Post by drs305 on 2012-06-23
It sounds to me more a kernel problem than a grub problem. Nevertheless, if you install Boot Repair and click the "Recommended Repair" button if it's Grub-related this app will probably fix it.

If it doesn't, you can run the boot info script from the same app. We can look at the results and at least see if there is a problem with the Grub menuentries. Although it would not specifically point the blame at the kernel, it might eliminate Grub as being responsible.

Boot Repair link in my signature line.

---

### Post by decomp on 2012-06-25
ok I ran Boot Repair and I'm no longer getting 'error: font format error' etc. and I just get sent to the grub menu. If I choose the 3.2.0-25 kernel, then I get:
'error: cannot read the linux header.
error: you need to load the kernel first.'

but the font format error & no suitable mode is gone. Thank you! Here is the pastebin link it generated: [http://paste.ubuntu.com/1058572/]("http://paste.ubuntu.com/1058572/")

Now I'm just dealing with the kernel issue I guess.

---

### Post by drs305 on 2012-06-25
Your pastepin shows that you have other kernels available in the "Previous Linux versions" submenu.

Boot into one of the working kernels and purge/reinstall "linux-image-generic" and see if that creates a usable kernel.
```

uname -r # Confirm you are using an earlier kernel
sudo apt-get purge linux-image-3.2.0-25-generic linux-headers-3.2.0-25-generic
sudo apt-get install linux-image-generic linux-headers-generic

```

---

