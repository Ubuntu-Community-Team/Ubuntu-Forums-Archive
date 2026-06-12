---
title: "Lost WinXP after Ubuntu Recover"
date: 2006-04-24
forum: General Help
---

### Post by megahertza on 2006-04-24
This is how the story goes. I had a dual boot WinXP Home and Ubuntu Breezy. I formated WinXP home drive and installed WinXP Pro Corp in its place. After loosing Grub, I used the rescue mode from the ubuntu install cd to recover grub and breezy. I now have Breezy booting fine, problem is WinXp Pro Corp is failing to boot from Grub.

I think grub is using old boot info for the WinXP HOME to boot WinXP PRO. I believe this is the cas because in the boot Menu is has Windows XP HOME as an item and not PRO. 

XP is on (HD0,0)

---

### Post by Qrk on 2006-04-24
Hmm. I am no expert on Grub, but it might be a problem with chainloader

Try looking at /boot/grub/menu.lst the Windows section of the file.

```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Is there a +1 for the chainloader part?

---

### Post by megahertza on 2006-04-24
This is what mine looks like.
```

title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

But title should be "Microsoft Windows XP Professional" Still title really isn't importent

---

### Post by Qrk on 2006-04-24
Backup the file before making any changes... Grub is very very important. 

Everything I know about grub I learned by installing Gentoo, which isn't much.
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10#doc_chap2](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10#doc_chap2)

From that document, it seems like you might want to change the portion of Grub to read like this:

```

title		Microsoft Windows XP Home Edition
rootnoverify		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Really, those are the only two parts of Grub I know how to change to boot windows. Half of my Gentoo installations wouldn't boot windows untill I did one or the other.

---

### Post by incubus on 2006-04-24
Are you sure your partition numbers didn't change?

Can you double-check through:
$ sudo fdisk -l

incubus

---

### Post by megahertza on 2006-04-24
I didn't get to check because i allready fixed the problem, allthou i don't know what was causing it, its now fixed. I used the windows install cd to recover my windows with FIXBOOT and then I used the ubuntu cd to fix grub in rescue mode.
> 
Can you double-check through:
$ sudo fdisk -l


FIXBOOT did say there was a error in the partition but didn't say what, it still worked thou.

---

### Post by pitkali on 2006-04-24
Perhaps Windows simply screwed up its own bootloader ;)

---

### Post by incubus on 2006-04-24
[QUOTE=megahertza]
FIXBOOT did say there was a error in the partition but didn't say what, it still worked thou.[/QUOTE]

Hmm. Be sure to backup your important files, just in case.

incubus

---

