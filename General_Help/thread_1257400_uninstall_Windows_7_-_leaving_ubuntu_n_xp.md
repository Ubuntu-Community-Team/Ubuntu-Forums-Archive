---
title: "uninstall Windows 7 - leaving ubuntu n xp"
date: 2009-09-03
forum: General Help
---

### Post by lovelife53 on 2009-09-03
*I'm havin three OS'es. Ubuntu + XP + Windows 7. Can anyone tell me how to uninstall windows 7, leaving behind ubuntu n xp ??*
*When my pc boots, grub shows the list of OS, ubuntu @ the top and then @ the bottom I can find Windows one. When I click on Windows, I find Windows 7 and XP.*
*I hope the above can prove useful. Just hoping..! lOlZZ*
*Whoever replies, please tell me what more information you need to resolve this issue..!*
*Thanks in Advance..! *

---

### Post by louieb on 2009-09-03
Hello again.  
Just a guess you had Ubuntu and XP installed when you installed Win 7. 
Win 7 put its boot loader in XP or hope just an entry in c:/boot.ini.

Anyway would like for you to download the [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") 

and unless you've changed the default Firefox download location heres how to run it.
Open Applications>Accessories>Terminal - cut and paste this command.

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

