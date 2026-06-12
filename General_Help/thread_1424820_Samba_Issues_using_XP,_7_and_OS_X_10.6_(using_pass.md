---
title: "Samba Issues using XP, 7 and OS X 10.6 (using passwords)"
date: 2010-03-08
forum: General Help
---

### Post by ldclan on 2010-03-08
Hi everyone, I really could use some help.

I have a Ubuntu PC setup sharing files via the gui (see Screenshot1.png) using the "Folder Sharing" options.

Right now I have the check boxes for "Share this folder", "Allow others to create and delete file/folders", and the " Allow Guest access" checked.
The Share name is "graphics-nas". 

My problem is this, the PCs that are connecting to it cannot unless the check box for Guest Access is marked.

If I uncheck the Guest Access and setup local accounts on the Ubuntu box for individuals to login. The Windows 7 PCs work sometimes (using different crendentials), the XP PCs do not at all and the OS X 10.6 just spins and then the share isn't mounted. But it can see the share.
Strange.

Now in the smb.conf file I have not setup the share there since the "Gui" share is showing up on the network. So my question is do I need to setup the share in the smb.conf file, use local accounts or something else?

I really need to setup a secured share on the "/media/NAS_Disk-2/graphic-nas", so everyone isn't connecting to it.  Thank you all any help would be greatful.

Ldclan

---

