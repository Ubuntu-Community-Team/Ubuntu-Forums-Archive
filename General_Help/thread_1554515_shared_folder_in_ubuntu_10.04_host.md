---
title: "shared folder in ubuntu 10.04 host"
date: 2010-08-16
forum: General Help
---

### Post by th1bill on 2010-08-16
I have just done a fresh install of Ubuntu 10.04 and downloaded the latest VBox onto my new 320 gig SATA HDD. I have installed WindowsXP and I have created the folder, "Shared," in my Home directory and created the shares for it, both by right click>share this folder and by Properties>Permissions but after finding the folder in Windows and creating the link I receive the following message;

    \\VBOXSVR\Shared is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

    The network name cannot be found.


This is the first time I've had this issue but after last night and today, if I had any hair left I would pull it out!

Help please.

---

### Post by Ginsu543 on 2010-08-16
Instead of setting up your Shared folder as a samba share, try setting it up as a shared folder inside VirtualBox. For your virtual machine, click on Settings. Click on the Shared Folders tab. Create a shared folder by clicking on the folder icon with a plus on it. Point this new shared folder to the Shared folder you have in your home folder.

Now, boot into Windows. Go to My Network Places. Click on Entire Network. Click on VirtualBox Shared Folders. You should see your new Shared folder there (\\VBOXSVR\Shared). For easy access, right click on it, select Map Network Drive.... Now you'll be able to see the drive in your My Computer and access it there.

---

