---
title: "admistration- grub"
date: 2009-07-01
forum: General Help
---

### Post by konnorrigby on 2009-07-01
i was just woundering if it is posible to edit the grub menu. i know theres a way with a editor. i dont recal the name of it.
 
i have googled it but all i found was the terminal way or the snyapic way. 
 
my problom is that i am on dial up and i cant hook it up corectly. i know but i am dual booting with windows.

---

### Post by abhi_69 on 2009-07-02
u can do this via gedit. just open terminal & become root.
then type-
**********
#nautilus
**********
this will open nautilus with root mode, go to- /boot/grub/menu.lst & right click>open with>text editor to edit & save it.
or u can try-
**********
$ sudo apt-get install startupmanager
*********
then, u will find it in system->administration->startupmanager
this software will do everything for u to edit grub menu in graphical mode
hope this will help u.

---

### Post by egalvan on 2009-07-02
> **konnorrigby said:**
>  if it is possible to edit the grub menu. i know theres a way with a editor.
 
i have googled it but all i found was the terminal way or the synaptic way. 

Unclear what you mean here, but I'll give it a stab...

The GRUB menu is called menu.lst (that's a lower-case L, not a numeral 1).

On a default install, it resides in

/boot/grub/

You can edit the file directly using any text editor...
But you need root privilege to save the changes ...

In a terminal, I use

```
gksudo gedit /boot/grub/menu.lst
```

Also, you can configure Nautilus to start in "Administrative Mode" option...
then navigate to the file location, and open menu.lst in Administrative Mode.
(I don't recall exactly how I did that under Hardy...
I believe it was a plug-in.
There are also scripts available.)

You can also use "Start-up Manager" to edit some (not all) of the options in menu.lst.
Under Synaptic, search for "startupmanager".
Once installed, it will show up under
System -> Administration

>  
my problem is that i am on dial up and i cant hook it up correctly.
i know but i am dual booting with windows.

I don't know what you are talking about here... sorry.

---

