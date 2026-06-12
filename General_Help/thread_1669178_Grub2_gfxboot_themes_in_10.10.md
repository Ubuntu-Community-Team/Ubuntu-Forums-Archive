---
title: "Grub2 gfxboot themes in 10.10"
date: 2011-01-17
forum: General Help
---

### Post by gbladeCL on 2011-01-17
I spent the other day trying to figure out how to use themeing in grub2 with gfxboot. I've read all the grub-gfxboot threads such as [Howto: GfxBoot]("http://ubuntuforums.org/showthread.php?t=208855&highlight=grub+gfxboot"); however, they are all quite old and for grub not grub2. Help would be appreciated.

Info: I'm running a fresh 10.10.

What I Tried:
I've installed the following packages: gfxboot, gfxboot-dev, gfxboot-theme-ubuntu.

I make in /usr/share/gfxboot-theme-ubuntu/ and copy the resulting boot/message to /boot/grub/messages/message.ubuntu

Then I edit /etc/default/grub adding
```
gfxmenu /boot/grub/messages/message.ubuntu
```

When I try to update I get:
```
$ sudo update-grub
/etc/default/grub: 4: gfxmenu: not found
```

I've also tried the following in grub; it doesn't complain, but it doesn't work either:
```
gfxmenu=/boot/grub/messages/message.ubuntu
```

I've confirmed that I have /boot/grub/gfxmenu.mod leaving me completely stumped. I've also looked at the gfxboot man pages. From what I gather I should be able to do **gfxboot --new-theme THEME**, but I don't know how to get from gfxboot-theme-ubuntu to the directory structure called for in the man pages.

EDIT:
I'm not interested in replacing grub2 with burg at the moment.

---

### Post by esdi on 2011-02-11
Hello, 

I would also be interested in some help about this issue.
I tried burg and it is working fine but I would prefer to theme and use the official Ubuntu grub2.

---

### Post by yourwhiteshadow on 2011-02-13
> **esdi said:**
> Hello, 

I would also be interested in some help about this issue.
I tried burg and it is working fine but I would prefer to theme and use the official Ubuntu grub2.

i think you want to use burg manager.

---

