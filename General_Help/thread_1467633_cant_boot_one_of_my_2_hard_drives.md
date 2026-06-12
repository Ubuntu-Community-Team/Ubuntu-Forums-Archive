---
title: "cant boot one of my 2 hard drives"
date: 2010-04-30
forum: General Help
---

### Post by XsilverX on 2010-04-30
hi, i would like someone to help 
last night i install ubuntu on my pc while installin there was a windows reporting a grub installing error it saids " grub cant be installed here" and it gives me the choice to select where to install it,
the problem is that i have 2 HD one of 80GB and the other is 160GB in the 80 gb HD i have windows xp already isntalled and in the 160 GB HD i was installing ubuntu, i choose to install the grub in the 160 GB HD and now when i turn on my pc i can only access ubuntu is like if my HD with Win xp just disappear , i would like someone to help me please

---

### Post by scradock on 2010-04-30
> **XsilverX said:**
> hi, i would like someone to help 
last night i install ubuntu on my pc while installin there was a windows reporting a grub installing error it saids " grub cant be installed here" and it gives me the choice to select where to install it,
the problem is that i have 2 HD one of 80GB and the other is 160GB in the 80 gb HD i have windows xp already isntalled and in the 160 GB HD i was installing ubuntu, i choose to install the grub in the 160 GB HD and now when i turn on my pc i can only access ubuntu is like if my HD with Win xp just disappear , i would like someone to help me please
Boot into Ubuntu (I know, you don't have any other option, do you?) then open a terminal and run "sudo update-grub"

You should see a series of responses as grub2 finds the Ubuntu kernels and then the Win XP on the other drive.

Once it syas "Done" you should be able to re-boot and get your options (Ubuntu or WinXP) displayed. 

If you don't get a grub menu with options, try hitting "Esc" as the machine starts up - that might bring up the menu.

It's possible you have the grub options "Don't offer a choice" and "Automatically boot the first OS" set - if you can't get anywhere check "man grub", or come back for more advice.

---

