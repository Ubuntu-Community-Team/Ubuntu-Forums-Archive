---
title: "Questions about Virtual Box"
date: 2010-11-26
forum: General Help
---

### Post by BigCityCat on 2010-11-26
I set it up but I have a few questions. One how do I retrieve my mouse from the box. It says right control but I press right click control and it doesn't release my mouse.

Also I was able to set up win7 but the cd I have is only an upgrade cd so it would not accept my product key because I would need vista installed for the key to accept it and the vista cds I have are just recovery discs. Is all this going to matter? Is there a way around this or should I just upgrade my win7 to the full version and get a new product key?

---

### Post by BigCityCat on 2010-11-26
Also, how do I get full screen?

---

### Post by Old_Grey_Wolf on 2010-11-26
It is the Ctrl key on the right side of the keyboard, not right mouse button + Ctrl.

You need to install the VirtualBox Guest Additions if you want full screen to work properly.

---

### Post by nolag on 2010-11-26
Unless you have vista and want to install it then update there is not much of a way arround it, unless you can get a vista disk then upgrade.  To answer does it matter, I would have to ask you what you plan to do with the windows 7 on a VM.  Also is it fully installed, just asking for a windows 7 key?  If so then the only thing is it will annoy you once in a while, and you can not install genuine windows stuff.

---

### Post by Old_Grey_Wolf on 2010-11-26
> **BigCityCat said:**
> Also I was able to set up win7 but the cd I have is only an upgrade cd so it would not accept my product key because I would need vista installed for the key to accept it and the vista cds I have are just recovery discs. Is all this going to matter? Is there a way around this or should I just upgrade my win7 to the full version and get a new product key?

I have heard :wink: of people using the OEM CD's without problems in VirtualBox. You live in the US though.

---

### Post by andymorton on 2010-11-26
Have you thought about using Qemu (from the software centre)? I think it's easier to use that Virtualbox.

---

### Post by BigCityCat on 2010-11-26
> **nolag said:**
> Unless you have vista and want to install it then update there is not much of a way arround it, unless you can get a vista disk then upgrade.  To answer does it matter, I would have to ask you what you plan to do with the windows 7 on a VM.  Also is it fully installed, just asking for a windows 7 key?  If so then the only thing is it will annoy you once in a while, and you can not install genuine windows stuff.

Well I skipped the product key and it is working but I am expecting it to start asking me to validate at some point. All I really want to do is use it to access my office pc through citrix which I cant do in ubuntu.

Do I need to antivirus win7 in the box?

---

### Post by BigCityCat on 2010-11-26
Was able to use Citrix. I'm simply amazed at how good it works. I am about to chunk my dual boot. I only need windows for a few things. How would I install office 2007 from disc?

---

### Post by Old_Grey_Wolf on 2010-11-26
> **BigCityCat said:**
> 
Do I need to antivirus win7 in the box?

It would be a good idea to take the same precautions with a VM that you would take with a normal install. However, you can always reinstall the VM from the iso file if it gets infected.

---

### Post by Old_Grey_Wolf on 2010-11-26
> **BigCityCat said:**
> How would I install office 2007 from disc?

You should be able to start the Windows VM from VirtualBox. After it starts and Windows loads completely, select the Devices menu on the VirtualBox top panel, then select CD/DVD Devices, and then the Host Drive option. Navigate using the Windows menu or however you have it set up to Computer or My Computer where you can see the disk drives, cd/dvd drives, etc. Insert the Office 7 CD. It should show up after a few seconds. Click on the icon for the CD/DVD and Office 7 should start to load.

---

