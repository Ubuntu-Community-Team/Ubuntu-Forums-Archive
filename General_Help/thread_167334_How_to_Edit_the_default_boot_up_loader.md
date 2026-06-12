---
title: "How to Edit the default boot up loader???"
date: 2006-04-28
forum: General Help
---

### Post by minhaz4u on 2006-04-28
Im bored of the old Ubuntu boot up loader...Is there any way to edit and make a custom loader???
Any help would really b appreciated ;)

---

### Post by linuxfanatic1024 on 2006-04-28
Please don't cross-post. It is considered rude.

That aside, what do you mean?  Do you mean configuration file or do you mean editing the boot loader itself?

---

### Post by minhaz4u on 2006-04-28
> Please don't cross-post. It is considered rude.

Wht u mean by this???..i dint get it! 


Yeah...I meant editing the bootloader or replacing it with a new one

---

### Post by linuxfanatic1024 on 2006-04-28
Crossposting is posting the same message in multiple forums.

But anyway, I added color to my bootloader by adding this to /boot/grub/menu.lst
```
# Pretty colours
color cyan/blue white/blue
``` 
You can change to LILO, the older bootloader, if you really want to, but it's not considered a good idea because GRUB is more versatile.

If you want to get GRUB's source code, you can type this in:
```
apt-get source grub
``` and when you're done modifying that, you can type this to compile it from Grub's source code directory:
```
fakeroot ./debian/rules
``` 
 I hope this answered your question. If not, feel free to ask more questions.

---

### Post by elamericano on 2006-04-28
Crossposting is posting the same message to multiple forums (For example, Ubuntu 5.10 Support and Absolute Beginner Talk)

Anyway, Normally I like LILO. It has an option to show a graphical screen from which to make the selections. However, for some reason it was a lot slower for me to boot with Ubuntu (someone tell me if this is normal)

I wouldn't bother with dumb colored text. Just replace the Ubuntu splash graphic with someting you like more. I can't imagine you'd replace your bootloader just because you're bored. You're talking about the image, right?

---

### Post by linuxfanatic1024 on 2006-04-28
[quote=elamericano]Crossposting is posting the same message to multiple forums (For example, Ubuntu 5.10 Support and Absolute Beginner Talk)

Anyway, Normally I like LILO. It has an option to show a graphical screen from which to make the selections. However, for some reason it was a lot slower for me to boot with Ubuntu (someone tell me if this is normal)

I wouldn't bother with dumb colored text. Just replace the Ubuntu splash graphic with someting you like more. I can't imagine you'd replace your bootloader just because you're bored. You're talking about the image, right?[/quote] What's slower about LILO?

---

### Post by elamericano on 2006-05-01
I'd have to go back to it and troubleshoot. I didn't see the bootup hanging on any step, but it was a lot longer to the login screen. I need LILO to be able to change the active partition (lilo -A /dev/hda 1), but I don't really care if I use it as my bootloader on this machine.

---

