---
title: "Unable to boot: Stuck at Grub command prompt"
date: 2010-02-12
forum: General Help
---

### Post by kdb8dm on 2010-02-12
Hi all,
i have been using ubuntu 9.10 without any problems for the last two weeks. However, when i booted my system today, it gets stuck at the grub command prompt. I was able to see the boot options, windows or Ubuntu, and on choosing Ubuntu, I got the Grub command prompt. 

The grub version is 1.97 beta 4. i do not know how to load Ubuntu from this. 

Can anyone help ?

Thanks,
K.

---

### Post by jerrrys on 2010-02-13
when you get grub boot option go back one kernel and see if it works

---

### Post by kdb8dm on 2010-02-13
> **jerrrys said:**
> when you get grub boot option go back one kernel and see if it works

I do not know what this means. Like i said before, while booting, i just get two options, windows and ubuntu, and on choosing ubuntu, i get the grub command prompt.

K.

---

### Post by drs305 on 2010-02-13
kdb8dm,

Welcome to Ubuntu and the Ubuntu forums.

You can try to fix it yourself by editing either the Grub 2 menuentry or dropping to the Grub 2 command line by following the instructions found here:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")

Or you can run meierfra.'s  [boot info script]("http://bootinfoscript.sourceforge.net/") and posting the RESULTS.txt contents will tell us what we need to know to fix your system. You can run it from the LiveCD. Please post the contents within 'code tags' (use the # symbol in the menu).

**Added:** What he meant was that if you have an older kernel listed in your menu listings for Ubuntu (lower than the first Ubuntu entry and having a lower kernel number. So if you have -19 first and -17 as another choice, try the -17 entry), try selecting that one to see if your system will boot.

---

### Post by BigG123 on 2010-02-13
Reinstall Everything N' format your whole drive.

---

### Post by kdb8dm on 2010-02-13
> **drs305 said:**
> kdb8dm,

Welcome to Ubuntu and the Ubuntu forums.

You can try to fix it yourself by editing either the Grub 2 menuentry or dropping to the Grub 2 command line by following the instructions found here:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

Or you can run meierfra.'s  [boot info script]("http://bootinfoscript.sourceforge.net/") and posting the RESULTS.txt contents will tell us what we need to know to fix your system. You can run it from the LiveCD. Please post the contents within 'code tags' (use the # symbol in the menu).

**Added:** What he meant was that if you have an older kernel listed in your menu listings for Ubuntu (lower than the first Ubuntu entry and having a lower kernel number. So if you have -19 first and -17 as another choice, try the -17 entry), try selecting that one to see if your system will boot.

Thanks for the link. For the moment, i just reinstalled ubuntu, got rid of windows and the original ubuntu. i am a recent convert and have been using ubuntu for just over  1 month. As such, i had a backup of most of the data anyway.

I am still uncertain as to what caused this ? I recall, there were some updates this week for ubuntu and when i installed them, i was prompted to reboot. On rebooting, i never got my system back. 

Thanks for all the replies though.

K.

---

