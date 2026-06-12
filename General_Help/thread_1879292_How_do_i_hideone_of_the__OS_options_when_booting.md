---
title: "How do i hideone of the  OS options when booting ?"
date: 2011-11-11
forum: General Help
---

### Post by famutshi on 2011-11-11
Hi everyone,

I have recently installed Ubuntu 11.10 in dual boot with windows 7 on my laptop. What do i do if i want to hide one of the option such as windows 7 (recovery) at the start menu ?

Thank you in advance for your help

---

### Post by Frogs Hair on 2011-11-11
Hello and Welcome 

Although changing the boot order may be possible I don't think hiding a boot option is .

---

### Post by grahammechanical on 2011-11-11
If you hide Windows (recovery) from the menu, what do you do when you need to use Windows recovery?

You could try installing Grub-Customizer. I use that to hide menu entries. I do not use Windows so I cannot say what Grub-Customizer will do to a Windows entry in the Grub menu.

I keep one Ubuntu recovery option in my menu list just in case. Find out what to do if you remove Windows recovery or Ubuntu recovery and then need to use it.

Here is a link to Grub-customizer.

[http://ubuntuforums.org/showthread.php?p=10340183]("http://ubuntuforums.org/showthread.php?p=10340183")

I find this a very useful utility. I have used it for a couple or years. It will do what you want and make it easy.

Regards.

---

### Post by btindie on 2011-11-11
It's not so much of the case of hiding it, it's getting grub to ignore that entry and not create a menu entry for it.

The scripts that generate the grub config file are located in /etc/grub.d

You can disable the use of a script by removing the eXecutable bit on the file ```
chmod -x <filename>
```If you know anything about scripting you could customise the script so it ignores the recovery partition, I think the one you'll want is 30_os-prober.

Once done run "sudo update-grub", you can then look at /boot/grub/grub.cfg to see the result.

I've done similar in the past to rename what it uses for the windows partition.

It may take some trial and error to get the result you want so it's probably better to work on a copy, e.g. ```
sudo cp /etc/grub.d/30_os-prober /etc/grub.d/31_os-prober
``` and edit that file instead, you'll then get duplicate entries but once you're happy with it you can disable the old script ```
chmod -x 30_os-prober
```

Edit: see [http://ubuntuforums.org/showthread.php?t=1362466](http://ubuntuforums.org/showthread.php?t=1362466) [http://ubuntuforums.org/showthread.php?t=1658997](http://ubuntuforums.org/showthread.php?t=1658997)

---

### Post by philinux on 2011-11-11
> **famutshi said:**
> Hi everyone,

I have recently installed Ubuntu 11.10 in dual boot with windows 7 on my laptop. What do i do if i want to hide one of the option such as windows 7 (recovery) at the start menu ?

Thank you in advance for your help

 [http://ubuntuforums.org/showthread.php?t=1362466](http://ubuntuforums.org/showthread.php?t=1362466)

Another alternative would be to password protect the recovery option.

---

