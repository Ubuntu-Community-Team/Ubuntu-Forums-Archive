---
title: "Automatix"
date: 2006-04-22
forum: General Help
---

### Post by kookookachooo on 2006-04-22
Hi, i just recently transfered to linux from windows XP going with the total wipe out of  windows. Ive been trying to use automatix and i keep getting this msg, "if you choose to install wine, please run winecfg to configure wine after automatix exits!" waht does this mean? im pretty sure i have wine, could someone help me or point me in the right direction of help on this issue? thank in advanced:)

---

### Post by OffHand on 2006-04-22
Open a Terminal and type: ```
winecfg
``` A screen will appear where you can configure Wine.

---

### Post by kookookachooo on 2006-04-22
thanks, but once i entered it i got "Warning: could not find DOS drive for current working directory '/home/richard', starting in the Windows directory." but the winecfg still came on. Once the configuration window came up (im guessing i add automatix in the "add application" box) nothing came up for me to select and the terminal said 

err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\richard\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\richard\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\richard\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\richard\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\richard\\Desktop"'.
err:commdlg:IShellBrowserImpl_BrowseObject could not browse to folder

what do i? or was i doing it wrong, thanks in adv.

---

### Post by adamkane on 2006-04-22
Do you have Wine installed?

If not, then ignore the winecfg message.

---

### Post by kookookachooo on 2006-04-23
thanks and im pretty sure i have wine installed. after the:

Warning: could not find DOS drive for current working directory '/home/richard', starting in the Windows directory.

the wine config still proceeds. is there something wrong with wine?thanks in adv.

---

