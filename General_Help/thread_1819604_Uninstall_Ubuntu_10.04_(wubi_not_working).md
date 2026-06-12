---
title: "Uninstall Ubuntu 10.04 (wubi not working)"
date: 2011-08-06
forum: General Help
---

### Post by RastaCalavera on 2011-08-06
Hello!

My sister has a sony vaio that currently is dual booting Ubuntu and Windows 7. I believe Ubuntu was installed using the wubi installer because I saw the uninstall-wubi application in the ubuntu folder. I clicked it and nothing happened. I right clicked it and did run as administrator and nothing happened. So what should I do next?

There is only one HD and ubuntu is on a 30gb partition. The grub is version 1.98 and the kernel is 2.6.32-22. I have read about running the fxmbr in windows but does that just wipe away grub? She is running out of space on her HD and I want to get the 30gb back to her. 

Anyone have a solution or a link to one? Help would be greatly appreciated! 

THANKS :)

---

### Post by jmszr on 2011-08-06
RastaCalavera,

This will explain it to you: [https://wiki.ubuntu.com/WubiGuide#How_do_I_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_uninstall_Wubi.3F) . Basically, in Windows you need to run the uninstaller in "Control Panel > Add or Remove Programs" for Windows XP or lower or "Control Panel > Programs and Features" for Windows Vista or Windows 7.

Hope that helps.

---

### Post by RastaCalavera on 2011-08-07
Thanks for the reply but there is not any "Ubuntu" under the programs and features. Is it possible that Ubuntu was installed using a live cd/usb but there is still a wubi in the ubuntu folder? I will attach some pictures to see if that helps

---

### Post by Rubi1200 on 2011-08-07
From the same guide:
> If the uninstaller fails, try downloading and running [Uninstall-Ubuntu.exe]("https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=Uninstall-Ubuntu.exe"). 

If that still doesn't help post back again.

---

### Post by RastaCalavera on 2011-08-07
I also jumped into the command prompt to see if that would work (the wubi guide said you could try to run this command if nothing I else worked) and here is what I got,

"User account control do you want to allow programs to make changes to your computer"

I clicked yes, so far this is the same as "run program as admin"

After clicking yes i get the loading circle next to the cursor but nothing happens.

ideas?

---

### Post by RastaCalavera on 2011-08-07
> **RastaCalavera said:**
> I also jumped into the command prompt to see if that would work (the wubi guide said you could try to run this command if nothing I else worked) and here is what I got,

"User account control do you want to allow programs to make changes to your computer"

I clicked yes, so far this is the same as "run program as admin"

After clicking yes i get the loading circle next to the cursor but nothing happens.

ideas?


the pic didn't attach i am trying again

---

### Post by mendhak on 2011-08-07
You can put your Windows 7 DVD in, go into startup recovery's commandline and try

bootrec /fixmbr

You can then boot into Windows and have a look at disk management, the Ubuntu partition will be an 'unknown volume' to Windows, you can simply make it another partition in Windows using FAT/NTFS.

---

### Post by RastaCalavera on 2011-08-09
Thanks for all the help unfortunately I didnt get to try all the solutions before i had to leave. I will mark this as solved until i visit her again

---

