---
title: "Use virtualbox image from different OS"
date: 2012-08-20
forum: General Help
---

### Post by lidewei on 2012-08-20
Right now I am using Kubuntu which is on sda. I have several .vdi files which are on sdb. I want to wipe Kubuntu and install Debian but I'm wondering if I can still use those .vdi files if I do that. These are actually my brothers vm's for school so I don't want to mess things up. Is there anything I can do that wil preserve those vm's?
I would appreciate any input or pointers in the right direction. =)

---

### Post by marlow59 on 2012-08-20
You can try to import your VM data and reexport it after reinstalling debian and the virtual machine : 
use the "Appliance Export Wizard" in VirtualBox to export your VM and then import it again on your reinstalled system. I'm using VirtualBox 4.1.8, but this feature has been around for at least a couple of versions.

                   Exporting a VM :

Open VirtualBox

Go to the File menu and select Export Appliance

Select the virtual machine (VM) you want to export and click Next

Choose where you will save the exported VM and click Next

Review settings and click Export

Copy the exported VM to an external hardrive (or put it on a partition that will survive the reinstall). Once you've reinstalled, you can import the VM.

                 Importing a VM :

Open Virtualbox

Go to the File menu and select Import Appliance

Choose the file to import and follow the rest of the prompts.

---

### Post by lidewei on 2012-08-20
Thank you for giving detailed instructions!
Just to be on the safe side: have you actually done this yourself? I have to be 100% sure it will work because there's no way to undo it if I mess things up. That would be fine if it was my own stuff but since this is my brother's stuff I really don't want to take any chances.

---

