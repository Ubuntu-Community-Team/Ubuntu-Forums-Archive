---
title: "Renaming VirtualBox Folder"
date: 2011-05-20
forum: General Help
---

### Post by jim_deadlock on 2011-05-20
All I want to do is rename the folder containing my VMs but when I do that it breaks the VMs. In the settings of the individual VMs under Storage, there is a location for the  .vdi file which I think may be the culprit but I see no way to change it. So is there a way to easily just rename the folder without importing/exporting the entire VM?

---

### Post by Aenima99x on 2011-05-20
Yes you can move/rename the folder holding the VM's.
1. Go to your home folder, then the **.VirtualBox** folder
2. Open the **VirtualBox.xml** with a text editor
3. Find the section titled **<MachineRegistry>**
4. Modify the path after **src="** to your new folder name
5. Find the section near the bottom starting with** <SystemProperties> **and change this path to your new folder name

---

### Post by jim_deadlock on 2011-05-20
Perfect thanks!

Now another thing, do you know how to set a shared clipboard so I can copy/paste between VM and host? I installed the extension pack but I can't see how to do it.

Edit: I see it in settings -> general -> advanced -> I have it set to bidirectional but it doesn't seem to work.

Edit #2: I think I need to install guest additions, now if I can just find out where to get them...

---

### Post by Irony on 2011-05-20
Install guest additions either from synaptic or at the top of the virtualbox screen where it says install guest additions.

---

### Post by rewyllys on 2011-05-20
> **jim_deadlock said:**
> . . . . Edit #2: I think I need to install guest additions, now if I can just find out where to get them...
Use Administration > Synaptic Package Manager.  Then in Synaptic's Quick filter window enter "virtualbox-guest-additions"; once it has been found, mark it for installation; and click on Apply.

---

### Post by jim_deadlock on 2011-05-20
Thanks, looks like I skipped the easy way, I've been messing around mounting ISO images and stuff, got it sorted anyway.

Edit: I just tried that method and it's telling me I have to remove virtualbox-4.0 in order to install it, so I think I'll stick with my original messing around method :) I forgot to mention I don't have the OSE version from the repository, I have the one off the VB website.

---

