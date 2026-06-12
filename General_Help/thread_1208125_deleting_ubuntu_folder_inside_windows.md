---
title: "deleting ubuntu folder inside windows"
date: 2009-07-08
forum: General Help
---

### Post by ibrabeicker on 2009-07-08
hi

i started to use ubuntu and i didnt knew how to install it so i installed while running windows xp, now i have just 1 partition and an ubuntu folder in my C: with only 17 gb, and I need more space now, so i need to know

**1 - can i delete this C:/ubuntu folder(does this remove linux completely?), create a second partition in my hd and install ubuntu again in this partition **

or

[B]2 - an easy way to increase this ubuntu folder, more precisely the root.disk file, so i can use more space in my unpartitioned disk
[/B]
thanks

---

### Post by raymondh on 2009-07-08
> **ibrabeicker said:**
> hi

i started to use ubuntu and i didnt knew how to install it so i installed while running windows xp, now i have just 1 partition and an ubuntu folder in my C: with only 17 gb, and I need more space now, so i need to know

**1 - can i delete this C:/ubuntu folder(does this remove linux completely?), create a second partition in my hd and install ubuntu again in this partition **

or

[B]2 - an easy way to increase this ubuntu folder, more precisely the root.disk file, so i can use more space in my unpartitioned disk
[/B]
thanks

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

If you prefer to use WUBI, at the link I attached, browse the right side and there are instructions on how to increase the virtual disk as well as others.

You can also remove Ubuntu from windows as well as edit the boot.ini file to reflect just a windows OS (rather than having both windows and Ubuntu when it starts up).....  

From there, you can decide how much space you are going to shrink windows ... defrag windows .... boot into the liveCD .... install UBUNTU choosing a GUIDED RESIZE which will give you a sliding bar that actaully does tha partitioning for you.  All you do is just slide the bar to suit your preference.

Remember to back up your files first ... as always, there are no guarantees whenever you do partitioning work (even the automated GUIDED RESIZE).

Good luck.

---

### Post by ibrabeicker on 2009-07-08
> **raymondhenson said:**
> [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

If you prefer to use WUBI, at the link I attached, browse the right side and there are instructions on how to increase the virtual disk as well as others.

You can also remove Ubuntu from windows as well as edit the boot.ini file to reflect just a windows OS (rather than having both windows and Ubuntu when it starts up).....  

From there, you can decide how much space you are going to shrink windows ... defrag windows .... boot into the liveCD .... install UBUNTU choosing a GUIDED RESIZE which will give you a sliding bar that actaully does tha partitioning for you.  All you do is just slide the bar to suit your preference.

Remember to back up your files first ... as always, there are no guarantees whenever you do partitioning work (even the automated GUIDED RESIZE).

Good luck.

so if i delete the C:/ubuntu i will remove linux from my pc?

---

### Post by raymondh on 2009-07-08
[QUOTE=ibrabeicker;7584988]so if i delete the C:/ubuntu i will remove linux from my pc?[/QUOTE

From re-reading the link I provided, I believe the proper way to uninstall Ubuntu is to uninstall it like a windows program ... from add/remove.

If you do that, then yes, you will remove linux from your system.

---

