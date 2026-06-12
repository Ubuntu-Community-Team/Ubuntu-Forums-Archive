---
title: "No password, no root access, no recovery mode"
date: 2012-01-15
forum: General Help
---

### Post by garandcarbine on 2012-01-15
Hi.
  So I got Ubuntu installed. Well, I did the stupid after installing it. I set the password to none. Now I have no root access. I did read the post about no root access, and it told me to go in to recovery mode. I did that. Except, it won't work. I have a wireless keyboard and mouse. But even with the extra wired one I have, it didn't work. I got in to recovery mode, but it doesn't respond to ANYTHING. I use the arrow keys, I press enter, I even tried ctrl+alt+del, nothing. Why doesn't my recovery mode work?

---

### Post by dcstar on 2012-01-16
> **garandcarbine said:**
> Hi.
  So I got Ubuntu installed. Well, I did the stupid after installing it. I set the password to none. Now I have no root access. I did read the post about no root access, and it told me to go in to recovery mode. I did that. Except, it won't work. I have a wireless keyboard and mouse. But even with the extra wired one I have, it didn't work. I got in to recovery mode, but it doesn't respond to ANYTHING. I use the arrow keys, I press enter, I even tried ctrl+alt+del, nothing. Why doesn't my recovery mode work?

There is **no** "root" access with a password or not in an Ubuntu system, log in with the username **you** were prompted for during installation.

---

### Post by Wug on 2012-01-16
I have not actually tried this but its worth mentioning since it might help.

It requires a bootloader of some sort, the instructions I read were for grub but its probably that it will work with others as well.  I'm not 100% sure how you could do it without one, apart from maybe installing one with a disk.

Boot to grub, and hit something (not enter :P) to stop the countdown.  Select the option you normally use, and press e to edit the boot parameters.  Add ' single' to the end of them.  Confirm and boot.  This will boot the system in single user mode.  You will end up at a prompt with root access.  from there you can change system passwords and settings as necessary.  When you're done, reboot.  The option is not permanent and when you reboot again, linux will boot normally (into multiuser mode).

Again, I have not tested this myself, but no harm should come from trying.

References:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[http://www.debuntu.org/recover-root-password-single-user-mode-and-grub](http://www.debuntu.org/recover-root-password-single-user-mode-and-grub)

Notes:
it might end up prompting for the root password.  if you dont know it, you might have to try something else.

See also:
I'm not sure if you could accomplish the same thing by booting with a rescue CD, chrooting to the regular root directory, and changing the root password.  Consider this an emergency measure, and consult with gurus before attempting.  I have never done it and if I can avoid it I never will.  This is purely hypothetical speculation.

---

