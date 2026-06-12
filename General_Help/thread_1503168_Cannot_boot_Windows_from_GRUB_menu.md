---
title: "Cannot boot Windows from GRUB menu"
date: 2010-06-06
forum: General Help
---

### Post by Claire Voyant on 2010-06-06
I upgraded to Ubuntu 10.04 recently and now have MBR problem. When selecting Windows XP from the 
GRUB menu the screen defaults to terminal mode with grub rescue> displayed. I admit I know little to nothing about Ubuntu, unix, etc other than I like what I have seen so far and am trying to learn more. I need to (unfortunately) use Windows and have data on it that I can't afford to lose. How can I repair the problem so I can boot Windows from the menu? Thank you

P.S. I was dual booting successfully earlier. I had the previous version of Ubuntu running with Win XP and everything was fine. The problem started when I upgraded to Ubuntu 10.04. I have tried reinstalling 10.04 with no success. If I am unable to get dual boot working my wish would be to save my Win data and then I can wipe clean and reinstall Win and Linux.
Thanks everyone for the help, I am trying all the suggested remedies.

---

### Post by skarme on 2010-06-06
As a last resort you can fix your MBR by using the Win Xp CD. This will delete GRUB and you'll directly boot to Win XP. You can then consider installing UBuntu 10.04 in a separate partition.

---

### Post by Leppie on 2010-06-06
could you download and run the boot info script and post the complete output?
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by Rubi1200 on 2010-06-06
This might help:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

See this too:

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Hope some of this helps.

:)

---

### Post by Claire Voyant on 2010-06-06
> **skarme said:**
> As a last resort you can fix your MBR by using the Win Xp CD. This will delete GRUB and you'll directly boot to Win XP. You can then consider installing UBuntu 10.04 in a separate partition.

Thank you, I should have mentioned that isn't working. When booting from Win CD everything stops and I get a "danger" message. I do appreciate your response

---

### Post by skarme on 2010-06-08
You mentioned saving your Win Data: Can't you access your Windows partition from Ubuntu?
I mean Ubuntu does show all partitions of the hard disk. Mount the Windows partition in Ubuntu; save the data from the Windows partition and then you can proceed with formatting your hard disk and subsequently installing the desired OS.

---

### Post by philinux on 2010-06-08
> **Claire Voyant said:**
> I upgraded to Ubuntu 10.04 recently and now have MBR problem. When selecting Windows XP from the 
GRUB menu the screen defaults to terminal mode with grub rescue> displayed. I admit I know little to nothing about Ubuntu, unix, etc other than I like what I have seen so far and am trying to learn more. I need to (unfortunately) use Windows and have data on it that I can't afford to lose. How can I repair the problem so I can boot Windows from the menu? Thank you

P.S. I was dual booting successfully earlier. I had the previous version of Ubuntu running with Win XP and everything was fine. The problem started when I upgraded to Ubuntu 10.04. I have tried reinstalling 10.04 with no success. If I am unable to get dual boot working my wish would be to save my Win data and then I can wipe clean and reinstall Win and Linux.
Thanks everyone for the help, I am trying all the suggested remedies.

Please see the General Help forum sticky post #2. This is a known fixable issue.

---

### Post by wilee-nilee on 2010-06-08
> **Leppie said:**
> could you download and run the boot info script and post the complete output?
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

This is what you want to do post it in code tags.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

And the general sticky post #2 is probably the answer but the script will confirm whats up, since you have tried to reinstall Ubuntu.

---

