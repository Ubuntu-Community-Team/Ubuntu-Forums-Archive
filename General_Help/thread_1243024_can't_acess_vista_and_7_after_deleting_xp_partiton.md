---
title: "can't acess vista and 7 after deleting xp partiton"
date: 2009-08-17
forum: General Help
---

### Post by Hyper Tails on 2009-08-17
hi I have vista 7 and ubuntu and I just deleted my xp partition and I for some reason can't access the vista loader and tried changing the hd path for the grub loader by kgrub (hd0,x) and It no use..

any help will be thanked

---

### Post by Hyper Tails on 2009-08-18
............................................................................

---

### Post by AmerNewbieInDE on 2009-08-18
did you have 4 partitions, each os to a partition? and xp was the first partition? i would guess you deleted you windows boot section.

---

### Post by Hyper Tails on 2009-08-18
i had 4 partitions

and it used the vista or 7,s boot loader and I don't know how this happened though

---

### Post by AmerNewbieInDE on 2009-08-18
with windows the boot loader is put in the begining section of the first partition. do you have install cd for vista or 7. was it the first partition that you deleted? when you boot with grub and chose windows install, i believe that it only points to the windows bootloader, grub doesnt actually boot windows.

---

### Post by Hyper Tails on 2009-08-18
yes i have a install cd of vista and 7

---

### Post by AmerNewbieInDE on 2009-08-18
where is your linux boot.. or are you using live cd

---

### Post by Hyper Tails on 2009-08-18
my linux boot is in /dev/sda6

---

### Post by AmerNewbieInDE on 2009-08-19
you can boot with your vista disk, choose recovery, and command prompt. run "fixmbr", but if grub is there, it will wipe it out. Any more i am at a loss, but this is the reason i keep windows and linux completely separate.

---

