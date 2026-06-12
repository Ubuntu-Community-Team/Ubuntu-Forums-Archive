---
title: "How to see old files from Secondary HDD in VirtualBox"
date: 2009-08-26
forum: General Help
---

### Post by sprilutsky on 2009-08-26
Hi,

I just installed VirtualBox on Ubuntu 9.04 and ran in an issue. 

My primary drive has Ubuntu OS with VirtualBox installed, running Windows XP. 

I also have a secondary hard drive with the existing data files, which I would like to be able to modify in either place: Ubuntu or VirtualBox Windows XP (not simultaniously of course)

Could not find the way to import/export my old data files from secondary HDD into VirtualBox and back. 

So for example: I have a folder "My Documents" on secondary HDD and would like to be able to edit one of the files int eh Windows XP editor on virtual box.

Does anyone know how to accomplish this? 

Your help is much appreciated

Thanks

---

### Post by VipX1 on 2009-08-26
If you open the file browser in Ubuntu and select the drive that you want to see in VirtualBox XP and Right click on it. Select 'Sharing Options' and give the share a name. Then tick the box to give Guest users access and click OK. Now right click the same drive folder again and select 'Properties'. Then select 'Permissions' and and the last entry 'Others' select 'Access Folders' Now go in to XP on the Vortual box. Go to the file browser in XP. Go to 'Tools' and 'Map Network Drive' and 'Browse' for your Ubuntu machine under the Microsoft Network. When you find your Ubuntu machine it should open and show you the Share, i.e. the drive you shared in Ubuntu. This will work because you ticked the box to allow others access to the folder in Ubuntu. 
I have set this drive to always connect at log in so reconnect everytime I start VirtualBox.
If you can't see the Share listed under the Ubuntu machine in the 'Map Network Drive' window try manually entering the Share. Example: \\Ubuntu-machine-name\Share-name
There is a similar example in the 'Map Network Folder' window.

---

