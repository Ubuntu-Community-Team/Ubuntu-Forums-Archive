---
title: "Reset Password - Ubuntu 9.10"
date: 2009-12-29
forum: General Help
---

### Post by megustamac on 2009-12-29
Hello, I have put Ubuntu 9.10 on my daughters Toshiba Satellite Pro and she has forgotten her password.  I have read the forums and instructions and tried all of the instructions so far (Press ESC, Press the Shift Key etc. etc but nothing interrupts the boot process and it just goes straight to the login/password screen.

I have also read it can be done via a live CD but I am not ashamed to say that although I prefer Linux to Windows for all the obvious reasons, when it comes to LInux and command line etc. I am a complete beginner and in the words of Manuel, I know nothing.

The Laptop originally had windows but I deleted all partitions and this is now a stand alone system, with one partition and one operating system only.

How can I access the recovery menu option?

TIA

---

### Post by s.fox on 2009-12-29
Hello,

[This]("http://www.psychocats.net/ubuntu/resetpassword") excellent guide tells you how to get into recovery mode and also reset the password.

Hope this proves useful.  If that does not work please post back.

-Silver Fox

---

### Post by drs305 on 2009-12-29
As Silver_fox said, try psychocat's link. He even has the way to show the menu in Karmic (holding down the SHIFT key).

One other thing that might be necessary if you are using Grub 2: If you display the menu and *do not* see a Recovery mode option, highlight the normal Ubuntu option, press "e", then highlight the "linux" line. That should display the actual linux command line. Cursor to the end of the line and add "single", then CTRL-X to boot. That should take you to the recovery mode.

---

### Post by sisco311 on 2009-12-29
> **drs305 said:**
> One other thing that might be necessary if you are using Grub 2: If you display the menu and *do not* see a Recovery mode option, highlight the normal Ubuntu option, press "e", then highlight the "linux" line. That should display the actual linux command line. Cursor to the end of the line and add "single", then CTRL-X to boot. That should take you to the recovery mode.

I would recommend to remove the *splash* kernel parameter. It may cause some problems in single user mode.

---

