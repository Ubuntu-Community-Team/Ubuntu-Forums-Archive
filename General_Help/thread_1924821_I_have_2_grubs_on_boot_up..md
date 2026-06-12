---
title: "I have 2 grubs on boot up."
date: 2012-02-13
forum: General Help
---

### Post by kittyhawk63 on 2012-02-13
OSes. Windows 7 and Ubuntu 11.10

I have used Wubi to install Ubuntu 11.10. I had Ubuntu 10.4 before installing 11.10. It was also installed using Wubi. I started installing Ubuntu 11.10 and it asked if I wanted to "uninstall" the earlier version. I clicked "yes." It did something rather quickly and proceeded to install 11.10. I rebooted after the installation, and now I have two Grubs. The first one only shows Windows 7. When I select it, it takes me into the second Grub. With that Grub, I see Windows 7 as default and Ubuntu 11.10 as secondary. That is the way I wish to see it.

Question. How do I get rid of the first Grub that only shows Windows 7 leaving me with the Grub that shows both Windows 7 and Ubuntu 11.10?

Thank you for your assistance in solving my problem. BTW, I have not used Ubuntu for a long time, so I am very rusty. My work keeps me primarily using Windows. I am brand new to Ubuntu 11.10. I am having to start all over again because things and names have changed. So, please be clear in telling me what I need to do to resolve this issue. Treat me like a brand new NOOB.

BTW, When I had version 10.4, I did not see "Ubuntu" listed in the "Remove Programs" section. I would have un-installed it there, if it had been listed.

Thank you again.
kh63

---

### Post by kittyhawk63 on 2012-02-13
Edit 1: I tried using MBRFix and nothing changed. I still have 2 Grubs.

Edit 2: I found this doing a seach: [http://askubuntu.com/questions/100586/how-do-i-access-a-wubi-install-after-installing-a-third-os-alongside-windows](http://askubuntu.com/questions/100586/how-do-i-access-a-wubi-install-after-installing-a-third-os-alongside-windows)

It seems this may be the way Wubi Ubuntu 11.10 does things. Wubi Ubuntu 10.4 only gave me one Grub.

Maybe there is nothing I can do to get rid of the first Grub.

If you know a solution and you know it works, you are still welcomed to post a reply. I will check by later to see if anyone offers a solution.

Thanks,
kh63

---

### Post by oldfred on 2012-02-13
Wubi boots with Windows, so the first menu you see is the Windows boot loader offering a choice of systems. In Windows (or grub for that matter) if you only have one system, you do not get a menu to choose since there is only one choice.

You may be able to set timeouts to now show the Windows menu, but if booting Windows you should use the first menu, not the grub menu.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by kittyhawk63 on 2012-02-13
> **oldfred said:**
> Wubi boots with Windows, so the first menu you see is the Windows boot loader offering a choice of systems. In Windows (or grub for that matter) if you only have one system, you do not get a menu to choose since there is only one choice.

Yes, I understand that Wubi boots with Windows. But, the **first **menu I get only offers me Windows 7. It does not offer me both Windows 7 and Ubuntu 11.10. I get that after I select Windows 7 in the first menu.

See if I can make this clearer. I apologize if I have not made myself clear.

Wubi Ubuntu 10.4 gave me **one** Grub menu to choose either Windows 7 or Ubuntu 10.4. It did not give me the first Grub menu that I am now seeing with Wubi Ubuntu 11.10. 

Wubi Ubuntu 11.10 gives me **two** Grub menus. The **first **Grub menu to select Windows 7 which takes me to the **second **Grub menu to select Windows 7 or Ubuntu 11.10.

I am wondering if I can get rid of the first Grub menu and have it exactly the way it was using Wubi Ubuntu 10.4.

Thank you for your information.
kh63

---

### Post by kittyhawk63 on 2012-02-13
Well, I went into Windows 7 and uninstalled Wubi Ubuntu 11.10. 

The **second **Grub menu was deleted leaving me with the **first **Grub menu that has Windows 7 listed. There should be **no **Grub at this point because _Wubi Ubuntu 11.10 was uninstalled_.

BTW, the **first **Grub was put there by Wubi Ubuntu 10.4. Wubi Ubuntu 11.10 supposedly deleted Wubi Ubuntu 10.4 when it installed. However, it is apparent it did not delete the Grub menu that Wubi Ubuntu 10.4 made.

Does anyone know how to get rid of this remaining Grub menu on boot up?

Thanks.
kh63

---

### Post by oldfred on 2012-02-13
If you are having a grub menu first do you also have a full install in a partition?

Post this from LiveCd or Ubuntu.

```
sudo fdisk -lu
```

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by kittyhawk63 on 2012-02-13
> **oldfred said:**
> If you are having a grub menu first do you also have a full install in a partition?

Post this from LiveCd or Ubuntu.

```
sudo fdisk -lu
```How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

No, this is not an install in a separate partition. This is using Wubi. It installs Linux like it were a program inside Windows.

Well, anyway, I have gone through the process of reinstalling each Ubuntu from version 10.4 onward until I am back to 11.10.  I still have the two Grubs, so I guess that is the way it sets itself up using Wubi. I never could get rid of the Grub with Windows 7 only. I just left it since it seems to be there using Wubi. It may take a complete reinstall of Windows 7 to get rid of it. I don't plan on doing that. At least, not anytime soon.

Thank you for your help. I will mark this solved, even though I was unable to fix my problem.

kh63

---

