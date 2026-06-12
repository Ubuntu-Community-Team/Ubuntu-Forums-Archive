---
title: "update ,stopped doesn't boot any more"
date: 2011-04-30
forum: General Help
---

### Post by Gianmaria on 2011-04-30
Hi

today i update ubuntu
someting was wrong
after 1 hour , the pc freeze , i rebooted 
and now it doesn't boot any more

the grub is working

ubuntu starts ,but told it can not mount the volume

i tried to run it in recovery mode and so on
nothing
it boot and stop during the boot

what could i do to restore it ?
i have not an image

thanks

---

### Post by kiyop on 2011-04-30
What is shown if you select "recovery (mode)" at Grub menu?

Did you installed Ubuntu with Wubi?

What version of Ubuntu have you used?

What version of Grub is shown during boot?

Do you remember the partition where Ubuntu was installed?

What will be shown if you press C key at GRUB screen and types:
```
ls
ls /
```If you have Ubuntu or some other distro's LiveCD, you can backup files into external HDD or so, I think.

---

### Post by Gianmaria on 2011-04-30
> **kiyop said:**
> What is shown if you select "recovery (mode)" at Grub menu?

Did you installed Ubuntu with Wubi?

What version of Ubuntu have you used?

What version of Grub is shown during boot?

Do you remember the partition where Ubuntu was installed?

What will be shown if you press C key at GRUB screen and types:
```
ls
ls /
```If you have Ubuntu or some other distro's LiveCD, you can backup files into external HDD or so, I think.
hi

i have installed ubuntu desktop 10.10
grug 1.98-20100804 5ubuntu3 
2.6.35-28 generic pae

every time i try to boot ubuntu i got this message

disk is not present or ready
wait or press S skip mount M manual revovery

today ubuntu asked to me to update , i answer yes
during the installation , the system freeze and i had to reset the pc via hardware

thanks a lot for you help


> Did you installed Ubuntu with Wubi? i don't know what is wubi
> 
Do you remember the partition where Ubuntu was installed?
yes a second partition after windows xp

---

### Post by wilee-nilee on 2011-04-30
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by Gianmaria on 2011-04-30
> **wilee-nilee said:**
> So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.
i have windows partitions , can i loose them ?

i guess the update was going to update to 11.04v

thanks

---

### Post by kiyop on 2011-04-30
> **Gianmaria said:**
> i have windows partitions , can i loose them ?

i guess the update was going to update to 11.04v

thanks
Thanks for your reply (the above #3 and #5).
Even if you run boot info script, you will not lose your windows partitions.

Please do what wilee-nilee asked you.

And...
[quote=Gianmaria]wait or press S skip mount M manual revovery[/quote]
Type S or M and see what happens.

---

