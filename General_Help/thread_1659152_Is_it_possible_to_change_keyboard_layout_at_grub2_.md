---
title: "Is it possible to change keyboard layout at grub2 prompt?"
date: 2011-01-03
forum: General Help
---

### Post by ttakun on 2011-01-03
I was reading GRUB2 manual, and I have been playing around with it  a little bit (changing splash screen, normal & highlight color, trying some commands, ...) but I have a little problem typing commands at grub2 prompt (after pressing 'c' key in grub2 menu) as my keyboard is **spanish**, and it seems keyboard layout in grub2 prompt is **en-US**.
Is there anyway to change that?

I tried with (my linux system is in /dev/sda2):
```
insmod ext2
set locale_dir=(hd0,2)/boot/grub/locale
set lang=es
```

But that only changes the language of the menu and I suppose the language of grub2 messages. Am I correct?

Thanks in advance.

---

### Post by ttakun on 2011-01-07
Well, it seems it isn't possible right now.

It's in low urgency experimental development in Natty Narwhal

- Keyboard layout support (via grub-mklayout and grub-kbdcomp)

Found in: [https://launchpad.net/ubuntu/natty/+source/grub2/1.99~20101124-1ubuntu1]("https://launchpad.net/ubuntu/natty/+source/grub2/1.99~20101124-1ubuntu1")

[-o<

---

### Post by spinifex on 2011-11-25
It there an update on keyboard layout support for Grub2? 

I'm wanting to specify Colemak in the keytable; and it appears no one knows if this is possible or supported. 

Anyone know how to go about it?

---

