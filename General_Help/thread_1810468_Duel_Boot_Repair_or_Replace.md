---
title: "Duel Boot Repair or Replace ?"
date: 2011-07-23
forum: General Help
---

### Post by Geroman21 on 2011-07-23
Previously had  Duel Boot set up on my Computer  with Windows XP Pro installed First and then Ubuntu.
 
 Originally  it was just Two options listed to choose on start up when I  Booted up,  this was Windows XP Pro or Ubuntu , if I did nothing Windows  Xp Pro  would start Automatically after about 20 seconds.

Over time this Boot Menu has become messed up, I now have to scoll down  the bottom of the First screen select windows and then I have a second  Screen with Windows XP  or Ubuntu to choose from.  I want to clean this  up so I just have the one screen again with two Simple options Windows  or Ubuntu. 

I have included the Two Screen shots,  is it easy to repair this or do I need to reinstall the Boot screen ?

Thanks Alan

---

### Post by JRV on 2011-07-23
It's an easy fix.

Open synaptic (System=>Administration=>Synaptic Package Manager).

Search for "2.6.32-" (Without the quotes).

Mark all except 2.6.32-33 for complete removal.

---

### Post by westie457 on 2011-07-23
> **Geroman21 said:**
> Previously had  Duel Boot set up on my Computer  with Windows XP Pro installed First and then Ubuntu.
 
 Originally  it was just Two options listed to choose on start up when I  Booted up,  this was Windows XP Pro or Ubuntu , if I did nothing Windows  Xp Pro  would start Automatically after about 20 seconds.

Over time this Boot Menu has become messed up, I now have to scoll down  the bottom of the First screen select windows and then I have a second  Screen with Windows XP  or Ubuntu to choose from.  I want to clean this  up so I just have the one screen again with two Simple options Windows  or Ubuntu. 

I have included the Two Screen shots,  is it easy to repair this or do I need to reinstall the Boot screen ?

Thanks Alan
Hi it is relatively easy to tidy up. also it probably is easy to go back to the two options you want however without knowing exactly how you got to your current set up we are going to tidy it.

Here is the procedure.....

Boot into Ubuntu (the top on in the list.
Then go to System > Administration > Synaptic-Manager.
Press Search (not Quick-search) and in the box type 'Linux-headers' - without the quotes. Press enter.

When search has completed click on the small box located top-left of the list - it might have a 'S' in it. This will sort the list with the installed packages at the top (little green boxes). Now go through this list marking them for removal. As a suggestion leave the 2 latest ones alone (little green box). 

One of these is the current header and the other is the back up to use when things go wrong sometime in the future.

Click Apply.

Grub will automatically be updated each time a header is removed.
This will take a few minutes.

Good luck

---

### Post by coldraven on 2011-07-23
"When search has completed click on the small box located top-left of the  list - it might have a 'S' in it. This will sort the list with the  installed packages at the top"

Thanks westie457, I've been using Synaptic for three years and never spotted the "S"!
What exactly is the difference between "regular" and "quick" search?

---

### Post by westie457 on 2011-07-23
> **coldraven said:**
> "When search has completed click on the small box located top-left of the  list - it might have a 'S' in it. This will sort the list with the  installed packages at the top"

Thanks westie457, I've been using Synaptic for three years and never spotted the "S"!
What exactly is the difference between "regular" and "quick" search?

quick search is more or less exactly the same as clicking on any entry in the package-list window en then tyoing in the name of the one you want. Regular search looks in the title and description giving you more results for any search term.

As an example 'broadcom' in quick gives 6 results and in regular gives 9.

---

### Post by Quackers on 2011-07-23
If you don't want the Memtest entries run this in the terminal ```
sudo chmod -x /etc/grub.d/20_memtest86+
```

---

### Post by donaldsmith on 2011-07-23
You could boot up with a Linux distro  that allows you just to install grub i.e Gentoo, Debian, arch, Slackware etc. I am now to figure it out but you can  reinstall grub with the grub shell.

---

### Post by Geroman21 on 2011-07-24
That seemed to do the trick, it has cleaned up my screen, I only have about 4 lines to scroll down now to get to second screen if I want to log into Windows .

Thanks 
Much Appeciated

---

