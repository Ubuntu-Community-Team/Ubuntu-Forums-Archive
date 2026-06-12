---
title: "Changing Grub 2 to add xforcevesa"
date: 2009-11-28
forum: General Help
---

### Post by two00lbwaster on 2009-11-28
I have the issue as described at [**this**]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/445881") link.

However, I have no idea, even after reading the Grub 2 docs, how to change the Grub 2 configuration to automatically add -xforcevesa to the main boot option; and thus not having to edit the grub.lst like in the olden days after each kernel update.

---

### Post by two00lbwaster on 2009-11-28
Bump.

---

### Post by oldfred on 2009-11-28
You need to edit grub and add it to the [FONT=Bitstream Vera Sans Mono]GRUB_CMDLINE_LINUX= :

[/FONT][FONT=Bitstream Vera Sans Mono]gksudo gedit [/FONT]/etc/default/grub

[FONT=Bitstream Vera Sans Mono]http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#GRUB_CMDLINE_LINUX

[http://ubuntuforums.org/showthread.php?t=1307154](http://ubuntuforums.org/showthread.php?t=1307154)
[/FONT]

---

### Post by two00lbwaster on 2009-11-29
> **oldfred said:**
> You need to edit grub and add it to the [FONT=Bitstream Vera Sans Mono]GRUB_CMDLINE_LINUX= :

[/FONT][FONT=Bitstream Vera Sans Mono]gksudo gedit [/FONT]/etc/default/grub

[FONT=Bitstream Vera Sans Mono]http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#GRUB_CMDLINE_LINUX

[http://ubuntuforums.org/showthread.php?t=1307154](http://ubuntuforums.org/showthread.php?t=1307154)
[/FONT]

Thanks, but xforcevesa doesn't seem to work for me :(

---

