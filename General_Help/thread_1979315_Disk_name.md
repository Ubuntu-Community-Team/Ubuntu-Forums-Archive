---
title: "Disk name"
date: 2012-05-13
forum: General Help
---

### Post by KMJones1 on 2012-05-13
I have a secondary HDD (i.e. separate from the Ubuntu system disk) seen as:
/media/1069872d-4266-4931-bec4-393f42ad0442
Can I change this name to something more memorable?!

---

### Post by zombifier25 on 2012-05-13
Launch "Disk Utility" (search for it in Unity, or System menu if classic GNOME) Then choose your hard drive from the left panel, choose the partition you want to change, click "Edit Filesystem Label" then set the label to whatever you like.

---

### Post by KMJones1 on 2012-05-13
Thanks for this.
I can get to the Disk Utility, but the option to edit the label doesn't exist; only "Edit partition" which doesn't allow name change (box unaccessible). 
The system disk does have the edit label option, I see.
:confused:
PS Ignore the personal info under my name - I have Ubuntu 12.04, but I'm not allowed to change my information until I get to 50 posts!! How ridiculous!

---

### Post by PaulW2U on 2012-05-13
> **KMJones1 said:**
> Thanks for this.
I can get to the Disk Utility, but the option to edit the label doesn't exist; only "Edit partition" which doesn't allow name change (box unaccessible). 
The system disk does have the edit label option, I see.
:confused:

If the drive is mounted you'll need to unmount it. You can also use GParted to edit the label if you can't see the option in Disk Utility.

[QUOTE=KMJones1]
PS Ignore the personal info under my name - I have Ubuntu 12.04, but I'm not allowed to change my information until I get to 50 posts!! How ridiculous![/QUOTE]

See [http://ubuntuforums.org/showthread.php?t=1836816](http://ubuntuforums.org/showthread.php?t=1836816).

---

### Post by KMJones1 on 2012-05-13
Thanks - that works a treat!!
Also, thanks for the link to the stuff about amending personal data; I understand better now.

---

