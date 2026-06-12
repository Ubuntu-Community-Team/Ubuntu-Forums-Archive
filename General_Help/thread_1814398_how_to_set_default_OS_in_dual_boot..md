---
title: "how to set default OS in dual boot."
date: 2011-07-29
forum: General Help
---

### Post by sgrad on 2011-07-29
I installed Ubuntu 11.04 side by XP pro. When systems boots up it goes to a screen listing 5 choices to boot into. Ubuntu first and XP pro last. I set the delay start time to 30 sec. and the XP pro as the default OS using the start up manager. THe default delay works and waits for a key press, but the order of the list has not changed and the highlighted OS (ubuntu) is what starts if no key is pressed.
How can I fix this?
Please be specific I am very new to Ubuntu.:D
Thanks

---

### Post by linuxuser12345 on 2011-07-29
Go to the Ubuntu Software Center and install Start-Up Manager. Using this program you can choose your default OS.

---

### Post by Elfy on 2011-07-29
> The user can also select "saved" as an option, which will use the last successfully booted kernel/OS as the default selection.From this thread - [http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)


There is also grub customizer [http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

@linuxuser12345 - please read the whole post - you'll see that the OP has stated that > I set the delay start time to 30 sec. and the XP pro as the default OS using the start up manager. 

---

### Post by Mark Phelps on 2011-07-29
> **sgrad said:**
> ... I set the delay start time to 30 sec. and the XP pro as the default OS using the start up manager.

I have found that startup-manager does NOT work properly with 11.04 and GRUB 1.99RC.  Can't handle the nested menus that the new version of GRUB generates.

Better to use Grub-customizer.

---

### Post by Elfy on 2011-07-29
> **Mark Phelps said:**
>  Can't handle the nested menus that the new version of GRUB generates.

Better to use Grub-customizer.Is that what it is, thank you.

---

### Post by sgrad on 2011-07-29
I am the OP and need to know where do I find grub customizer. Does it re-order the default boot order in V11.04 & grub 1.99? That's what I am trying to fix. 
Thanks for all who have responded.
 
 
 
 
> **Mark Phelps said:**
> I have found that startup-manager does NOT work properly with 11.04 and GRUB 1.99RC. Can't handle the nested menus that the new version of GRUB generates.
 
Better to use Grub-customizer.

---

