---
title: "accessing windows filesystem!!"
date: 2009-07-06
forum: General Help
---

### Post by sububtu on 2009-07-06
Hiii

How can i access windows file formats???
it doesnt matter , merely acessing the filesystem...
can i hav write permission in those FS??

thanks in advance

---

### Post by earthpigg on 2009-07-06
any storage device you have plugged in will show up in places -> computer

yes, you can read/write to windows and DOS filesystems.

---

### Post by sububtu on 2009-07-06
yes i agree with uuu--
i do hav removable storage devices formatted in fat32- is accessible in both win and ubuntu environments..
but  i hav winxp ntfs (partitions X 4) i can only access them in readonly mode
Y?

---

### Post by lisati on 2009-07-06
You might have to enable NTFS support. From Applications->Add/Remove, make sure the software source button shows "All available applications"
Then do a search for "NTFS" (without the quotes) and select "NTFS Configuration tool". You might be asked something like "Enable community maintained software" - allow this. Then click "Apply changes" then "apply".
Once the software is installed, you can configure things - on 9.04 the relevant entry is on the System->Administration->NTFS Configuration Tool menu.

---

### Post by earthpigg on 2009-07-06
if what lisati just said does not work, please give us the exact error message it gives you when you try :)

---

### Post by sububtu on 2009-07-08
^^ Ur right!!
i was not able to install the package..
nothing happend,, 
i just saw some progressbar...
then i was not able to check the "checkbox" near to the "ntfsconfiguration tool"

---

