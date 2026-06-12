---
title: "Ubuntu won't boot up"
date: 2011-08-01
forum: General Help
---

### Post by rockinruler on 2011-08-01
Hey,
Thanks for looking in.

I have Ubuntu 10.04 and Win 7 on a dual boot config. My sister had been using my laptop for a week for her science project, and since the computer would boot into Ubuntu by default, she'd turn it off admist its booting process and start it again since she prefers Windows.

This turning off of the computer while Ubuntu was being booted quite a few times till one day it stopped booting properly.
Now all I get is a terminal-like screen instead of the GUI and I can't figure how to fix this.
I'm attaching a shot of the screen I see when I now try to boot into Ubuntu along with this thread.
Can someone please tell me how do I fix this?


[[IMG]http://img846.imageshack.us/img846/1537/30072011932.jpg[/IMG]](http://imageshack.us/photo/my-images/846/30072011932.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by Mark Phelps on 2011-08-02
Can you boot into anything? Or just not into Ubuntu.

What you can try ... hold down a SHIFT key while booting.  This should force the display of a GRUB text menu.  Select the top-most Recovery Mode option.  When it comes up, select the option to repair broken packages.  If that completes normally, select the option to boot normally.

If all goes well, you should be back at the desktop after reboot.

---

### Post by rockinruler on 2011-08-04
> **Mark Phelps said:**
> Can you boot into anything? Or just not into Ubuntu.

What you can try ... hold down a SHIFT key while booting.  This should force the display of a GRUB text menu.  Select the top-most Recovery Mode option.  When it comes up, select the option to repair broken packages.  If that completes normally, select the option to boot normally.

If all goes well, you should be back at the desktop after reboot.

That didn't work Mark.
Then I fixed it using the method shown here
[http://kuniganotas.wordpress.com/2010/11/02/error-on-mounting-dev-on-rootdev/](http://kuniganotas.wordpress.com/2010/11/02/error-on-mounting-dev-on-rootdev/)

Thanks for replying though Mark :)

---

