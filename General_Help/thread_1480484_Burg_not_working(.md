---
title: "Burg not working:("
date: 2010-05-11
forum: General Help
---

### Post by nbulchandani on 2010-05-11
hello,
I installed Burg succesfully.but on rebooting the same old grub screen appears;where am i wrong?
Thanks

---

### Post by nbulchandani on 2010-05-12
does anyone have any ideas?

---

### Post by nbulchandani on 2010-05-14
No one intrested in this thread?

---

### Post by warri0r on 2010-05-14
installed the themes?+

[http://code.google.com/p/burg/wiki/InstallUbuntu](http://code.google.com/p/burg/wiki/InstallUbuntu)
[http://ubuntuguide.net/decorate-grub-2-boot-loader-using-burg](http://ubuntuguide.net/decorate-grub-2-boot-loader-using-burg)

---

### Post by nbulchandani on 2010-05-14
whenever i do burg-install "(hd0)".it says installation finished succesfully.But when i reboot there are no boot options..i have to reinstall the grub again.also whenever i run burg-emu..the same screen without any boot options appears..this implies i am installing burg to the wrong partition ;so how do i determine the correct partition?
Thanks

---

### Post by nbulchandani on 2010-05-14
sudo grub-probe -t device /boot/grub
gives /dev/sda5
.when i run
sudo burg-install /dev/sda
it finishes succesfully;but burg-emu shows nothing but a grub CLI.and on reboot i suppose i would have to reinstall the grub.any help is admired.
Thanks

---

### Post by nbulchandani on 2010-05-14
Well fine i rectified it.Thanks for looking..

---

### Post by warri0r on 2010-05-14
glad it works. :)

---

### Post by Mi11z on 2011-03-30
I get this issue a lot after reinstalling windows, after I've switched back to grub from the windows boot loader I almost never seem to get burg working again, at least not for a while. =/

---

### Post by psycho on 2011-09-12
Hi nbulchandani. Just a comment on [SOLVED] threads: I understand that you may not feel like detailing your solutions on a forum when you didn't get much help with them from that forum...but don't forget, these posts stay on the Internet for years and may be read by hundreds or even thousands of people...so posting "I rectified it" without saying *how* you solved it can mean lots of people wasting their time reading through a thread that doesn't actually provide a solution.

I know it doesn't feel like it, but given that support forum posts are Googled so often, posting here is effectively publishing, and potentially to a very wide readership. So even if you solved a problem by yourself, it's nice to close off the thread with a brief summary of what you did (even if it's nothing more than five words, "I finally read the manual!", the information might help someone else).

:)

---

### Post by Forte125 on 2011-09-26
Same problem, could use help.

None of the shortcuts work and no theme is present.

---

