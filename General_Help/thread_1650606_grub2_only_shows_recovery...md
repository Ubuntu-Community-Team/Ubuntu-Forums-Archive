---
title: "grub2 only shows recovery.."
date: 2010-12-21
forum: General Help
---

### Post by sk8rjess on 2010-12-21
after messing around with plymouth manager to try and get a decent boot screen(for the 3 weeks i've had 10.10 installed, it's just been a plain text bootup) it seemed to have removed my main boot option without recovery.
i'm still able to boot into recovery and pull up my graphical environment but i can't seem to figure out how to get my normal boot option back.

---

### Post by wilee-nilee on 2010-12-22
> **sk8rjess said:**
> after messing around with plymouth manager to try and get a decent boot screen(for the 3 weeks i've had 10.10 installed, it's just been a plain text bootup) it seemed to have removed my main boot option without recovery.
i'm still able to boot into recovery and pull up my graphical environment but i can't seem to figure out how to get my normal boot option back.

So the grub menu only shows a recovery?

Are you dual booted, and have you installed startup manager in Ubuntu per chance?

---

### Post by sk8rjess on 2010-12-22
i am dual booted, yes.
and i only installed startup manager after all this happened.

---

### Post by wilee-nilee on 2010-12-22
> **sk8rjess said:**
> i am dual booted, yes.
and i only installed startup manager after all this happened.

How about the grub menu question?

---

### Post by sk8rjess on 2010-12-22
sorry, my choices are: 
ubuntu recovery
mem test
mem test serial console
windows 7

---

### Post by dino99 on 2010-12-22
which release are you running ?

sudo dpkg-reconfigure grub-pc

---

### Post by wilee-nilee on 2010-12-22
lets get the bootscript it will show a lot of stuff. So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

Try post 6 that may get you back in shape.

---

### Post by Linyx on 2010-12-22
> **dino99 said:**
> 
sudo dpkg-reconfigure grub-pc

[SIZE="2"]Sorry for inter-fairing in thread, but can i know what this command is use for...? To refresh Grub entries ..?[/SIZE]

---

### Post by wilee-nilee on 2010-12-22
> **Linyx said:**
> [SIZE="2"]Sorry for inter-fairing in thread, but can i know what this command is use for...? To refresh Grub entries ..?[/SIZE]

Here is a great link for grub2 commands look for yourself.
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html)

---

### Post by sk8rjess on 2010-12-22
thanks for the help guys, but on a reboot it fixed itself? weird.

---

