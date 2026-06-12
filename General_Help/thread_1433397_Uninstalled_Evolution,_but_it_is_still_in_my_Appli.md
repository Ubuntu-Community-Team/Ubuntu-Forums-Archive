---
title: "Uninstalled Evolution, but it is still in my Applications menu?"
date: 2010-03-19
forum: General Help
---

### Post by JMW4th on 2010-03-19
that's my current problem.  I installed Claws Mail, and tried to uninstall Evolution using "sudo apt-get remove evolution". apparently I uninstalled "some" of evolution but not all, because "Evolution Mail and Contacts" is still present in my Office menu. 

any idea what I did wrong here? I want Evolution completely gone.

---

### Post by gadolinio on 2010-03-19
In order to remove it from the aplications--office menu, go to System-->preferences-->main menu. Or press Alt+F2 to open a terminal, type "alacarte" and hit enter.  Both ways you'll now see a window where you can manage everything in your menu. So just go to applications, office, and erase evolution.
Before erasing it, double click it and see which command it executes, so that you know the programs exact name. If you are sure you want to delete it, you can do it from system-->administration-->synaptic package manager.

---

### Post by JMW4th on 2010-03-19
thanks for the response.

I've been reading a bit, and apparently you CAN'T *completely* delete evolution? i went to delete every evolution file in synaptic, but then it suggested that I delete pretty much the whole interface, pluse brasero and some other programs.

why is evolution integrated so much with the Ubuntu installation that it is so difficult to remove? no other packages have threatened to delete so much extra unrelated stuff.

---

### Post by gadolinio on 2010-03-19
Oh, yes, that happens with other programs too. For example, you can't uninstall Openoffice.org Base alone, cause you have to delete Impress too, and maybe something else. There's also some Thunderbird-related language packages that cannot be deleted without removing Openoffice's help as well. And if you want to uninstall Blackjack you have to accept doing the same with chess, Iagno, and others. Just a few examples.
I don't know any solution to this...

---

### Post by JMW4th on 2010-03-19
well, I uninstalled evolution, and when i rebooted my computer, my entire interface was broken and unusable. 

I re-installed evolution from the command line and now everything is fine.

I am not pleased with this. I'm being forced to keep software that I do not want and will not use on my machine in order for my computer to simply boot correctly. There is absolutely no reason why a specific email client should be that necessary for an operating system to run.

Evolution is the Internet Explorer of Ubuntu.

---

### Post by JMW4th on 2010-03-19
well, I uninstalled evolution, and when i rebooted my computer, my entire interface was broken and unusable. 

I re-installed evolution from the command line and now everything is fine.

I am not pleased with this. I'm being forced to keep software that I do not want and will not use on my machine in order for my computer to simply boot correctly. There is absolutely no reason why a specific email client should be that necessary for an operating system to run.

Evolution is the Internet Explorer of Ubuntu.

---

### Post by gadolinio on 2010-03-20
Mmm i think i removed it once, although only that package (no related ones). But i can't remember for sure...
In case you need to keep it, see it as an important dependence to other packages, as if it were some "libevolution-lksdñjfñlaskd" or something :P
Unselect it from you menu editor, so that it doesn't bother you by appearing there...
Forget that you have it installed in your system....
Good luck! :P

---

