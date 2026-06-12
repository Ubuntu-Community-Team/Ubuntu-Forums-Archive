---
title: "Can't Get Grub to Display"
date: 2010-08-04
forum: General Help
---

### Post by kernelles on 2010-08-04
Replaced XP on my mom's PC with Ubuntu 10.04. Can't get GRUB menu to display, just goes straight to splash screen. I'm trying to boot with an older kernel by pressing space bar to solve an Intel chip issue, but still just goes to login screen. Even pressing ESC does nothing.

---

### Post by oldfred on 2010-08-04
With the new version grub2 you have to hold down the shift key from BIOS till menu appears, if you only have Ubuntu on the system.

Escape was for grub legacy.

---

### Post by kernelles on 2010-08-04
> **oldfred said:**
> With the new version grub2 you have to hold down the shift key from BIOS till menu appears, if you only have Ubuntu on the system.

Escape was for grub legacy.

As I had mentioned in my post, I tried the shift key as well as esc, but neither is working. I have also tried to replace grub2 with grub legacy just to see if it would change anything, but no difference. 

Once, I got some error that mentioned something like "Glib" and said something failed due to an unknown user ID. There was a code that was given with this message of "247." Unsure if this is relevant. 

Thanks in advance.

---

### Post by kernelles on 2010-08-04
If there isn't a solution to my problem, does anyone know how I can downgrade from the 2.6.32 kernel to 2.6.31? All I really need to do is to boot up with this kernel, it's just that I can't get into the grub menu to select it. This would be an acceptable workaround. In other words, if 2.6.31 is the ONLY kernel installed, it will be forced to boot with it, which is really my goal.

---

### Post by oldfred on 2010-08-04
If you tried just to install grub over grub2 it may be more confused. They do not work well together. It is best to totally uninstall both and install one or the other. You can do this from chroot.

Your error does not sound like a grub boot error but run this to see if something looks out of place.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

You mentioned space not shift in first post.

---

