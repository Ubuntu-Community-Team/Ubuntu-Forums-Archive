---
title: "Installing ubuntu 12.04"
date: 2012-06-10
forum: General Help
---

### Post by hsaptus on 2012-06-10
I managed to try the live version with the the nolapic or acpi = off boot parameters. After i installed the OS now i can't boot with the same error i was getting. How can I pass those options to grub?
Thanks in advance.

---

### Post by sudodus on 2012-06-10
I think you will find explanations in this link
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1195275_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")
If you enter the boot options in the right place, it will survive the upgrades. See

5. Grub 2 files & options

---

### Post by hsaptus on 2012-06-10
so if i understood it correctly, i choose de e option in the grub menu of the system i want to load and in the parameters i want are added in the line:
linyx /boot/etc...etc... after the quiet splash acpi=off nolapic

---

### Post by hsaptus on 2012-06-10
Never mind :P, it was right on the spot :)
Thank you mate, it worked smoothly.

---

### Post by hsaptus on 2012-06-10
If i understood it right, i should edit the file /etc/default/grub

and add the in the following line:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" "acpi=off" "nolapic"
```if i do that, when i update the grup, i get this error:

"/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution"

Where is my mistake?
Thanks again

---

### Post by Karlchen on 2012-06-10
Hello, hsaptus.

I think the line should read ```
GRUB_CMDLINE_LINUX_DEFAULT="acpi=off nolapic quiet splash"
```There must be only 2 double quotes, 1 at the beginning and 1 at the end.

Kind regards,
Karl

---

### Post by hsaptus on 2012-06-10
That was it :)
Thanks again mate, you and _sudodus made my day :) . Love the new ububtu so far. Thanks a bunch_[URL="http://ubuntuforums.org/member.php?u=1499021"]
[/URL]

---

### Post by hsaptus on 2012-06-10
of course the 0-1 of last night was still pretty messy :P :D
Regards Karl

---

