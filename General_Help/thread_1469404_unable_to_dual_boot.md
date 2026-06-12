---
title: "unable to dual boot"
date: 2010-05-02
forum: General Help
---

### Post by unrealseal on 2010-05-02
i have upgraded to ubuntu 10.04 but now can't boot into win vista, ubuntu and vista are on grub but vista will not load, i have tried  sudo upgrade-grub which seemed to work but had no effect on loading windows
thanks for replys, did think of using win dvd to fixmbr but only as last resort, i entered the commands suggested by nitstorm and got "command not found"

followed nitstorm's advice followed link to source forge.net and test disk, followed the instructions to install and run test disk which repaired the boot sector in the vista partition, i can now choose to boot into win or ubuntu so many thanks nitstorm :)

---

### Post by skarme on 2010-05-02
@unrealseal:
What happens when you choose win vista? Did you upgrade to ubuntu 10.04 from an older version or you used a desktop-live CD?

---

### Post by Nick.Sth on 2010-05-02
I had problems such as that when installing 10.04 with Wubi, nothing would open, nor Vista nor Ubuntu idk why, so I opened Xp downloaded the iso image burnt it to a cd, and installed Ubuntu like that and everything worked. No idea why it worked but it did :P

---

### Post by unrealseal on 2010-05-02
> **unrealseal said:**
> i have upgraded to ubuntu 10.04 but now can't boot into win vista, ubuntu and vista are on grub but vista will not load, i have tried  sudo upgrade-grub which seemed to work but had no effect on loading windows

upgraded from 9.04 via cd using the upgrade option, vista appears in grub as before but when selected 9 (highlight and press enter) nothing happens then grub goes back to ubuntu selection

---

### Post by skarme on 2010-05-02
@[unrealseal]("http://ubuntuforums.org/member.php?u=1051457"):
Do you have a lot of stuff installed on Ubuntu which you don't want to loose? If 'NO' then you may try this but I recommend you wait for more suggestions and explore more on this issue.

Fix the boot record for Vista. In Windows Xp there is a command 'fixmbr' which lets you fix the boot record after entering the recovery console; not sure about vista, you may check the following link for the same

[http://www.vistaheads.com/forums/microsoft-public-windows-vista-general/26168-fix-mbr-vista.html](http://www.vistaheads.com/forums/microsoft-public-windows-vista-general/26168-fix-mbr-vista.html)

After you've done that, restart your PC and you should boot in vista straight away(the GRUB loader will go). Delete the partition for Ubuntu(i.e Deleting Ubuntu) and leave it as 'free space' and reinstall a fresh copy of ubuntu 10.04 on restarting the PC. GRUB and Ubuntu 10.04 will be freshly installed and things should work fine. 
(I presume that your Window's Vista worked fine and you haven't messed with the partition)

---

### Post by nitstorm on 2010-05-02
ubuntuforums.orgubuntuforums.org/newreply.php
can you please post the output of 
```

sudo osprober

```

and also post the results of the [bootinfoscript]("http://sourceforge.net/projects/bootinfoscript/") here please?

---

### Post by nitstorm on 2010-05-02
ubuntuforums.orgubuntuforums.org/editpost.php

you can also try [this]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") first.

---

