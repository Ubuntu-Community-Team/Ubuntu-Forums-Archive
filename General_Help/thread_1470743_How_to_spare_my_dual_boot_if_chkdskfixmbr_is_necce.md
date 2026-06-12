---
title: "How to spare my dual boot if chkdsk/fixmbr is neccessary to fix my XP system?"
date: 2010-05-03
forum: General Help
---

### Post by cyrylski on 2010-05-03
Hello, 

Today I faced a difficult dillemma:

as a result of power supply interruption my win XP session was interrupted. After restart I face a blue screen with a UNMOUNTABLE_BOOT_VOLUME error. The dilemma starts here: 

the solution for me is to run a chkdsk and fixmbr from Windows recovery mode. But, if I do that, I'll mess up my GRUB, as far as I know. If I do that, I won't be able to fix GRUB back because I have no CD drive in my laptop and I'm not sure if I'll be able to access my Ubuntu 10.4 partition and system after booting to windows. 

I have access to linux files systems (reiser and ext3 etc.) form windows thanks to very helpful driver utility :)

What I need to know is the following things: 

1) will chkdsk and fixmbr mess up my Ubuntu installation?
2) will I be able to fix my Ubuntu installation without a CD or a floppy?
3) is there a method of installing Ubuntu/any Linux on a hard drive to make it a dual boot afterwards without a CD or floppy drive? Maybe from another computer?

Please help me with these issues. I can't proceed without being 100% sure that I'll be able to keep a dual-boot in future.

---

### Post by spiky001 on 2010-05-03
you can use a usb to boot ubuntu check yor machine will boot from usb 1st

---

### Post by dino99 on 2010-05-03
steps to follow:

- repair xp
- grub need to be installed on ubuntu mbr partition ( not windows partition)
- sudo grub-mkconfig && update-grub

---

### Post by john newbuntu on 2010-05-03
Apparently there is also a network install that you can do from windows:
[https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot)

As evident, I have not tried it.

---

### Post by dino99 on 2010-05-03
unetbootin can help

---

