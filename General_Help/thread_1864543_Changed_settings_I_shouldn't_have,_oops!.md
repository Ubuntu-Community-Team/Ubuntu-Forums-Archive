---
title: "Changed settings I shouldn't have, oops!"
date: 2011-10-19
forum: General Help
---

### Post by hayden92 on 2011-10-19
Hey guys this is probably a stupid question:

I'm using Oneric and I was looking at the new 'System Settings'. I changed my user account from "Administrator" to "Standard". Unfortunately this means that now I can't install programs from apt; i.e. "sudo apt-get install <program>".

I can't change my account back to "Administrator" because I'm now locked out!

Any help would be greatly appreciated!

---

### Post by twipley on 2011-11-13
Same thing just happened to me. As you usually need an administrator account to create other administrator accounts, you are in trouble.

However, there is a solution. Reboot, holding shift to access the GRUB menu, then step into recovery mode, first remounting the file system, then booting to a root shell to "adduser <whoami_from_terminal> admin," and voilà -- you have found a solution to your locked-out problem.

thanks to nothingspecial -- [http://ubuntuforums.org/showpost.php?p=11384085&postcount=4](http://ubuntuforums.org/showpost.php?p=11384085&postcount=4)

---

### Post by hayden92 on 2011-11-20
Thanks mate, worked a treat!

---

