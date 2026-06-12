---
title: "Virtual Box XP USB wont work"
date: 2011-02-28
forum: General Help
---

### Post by pagunston on 2011-02-28
I have Ubuntu Installed on my laptop with XP installed inside a virtual machine. When I start XP, I can not access my USB. Please explain how to make XP recognize the USB. 

I am new to Ubuntu sorry.

---

### Post by An Sanct on 2011-02-28
Which version of Virtualbox are you running?

go to System > Administration > Users and Groups, click "Manage Groups", in the list, browse down to "vboxusers", select it and click "Properties", make sure that you are a member (and have a checked checkbox besides your name)

Maybe you will have to re-login to make the settings effect.

---

### Post by muteXe on 2011-02-28
Do you have the PUEL version of VB?
the one from the repo's will not have usb support you'll have to get the PUEL VB from their website I believe.

---

### Post by Kernelslave on 2011-02-28
Hey man, your problem is most likely having an OSE version of VB. Guessing you installed it through package manager.

Solution:
Remove the OSE go to the VB website and download the PUEL version (any from the download page)
If you are running MM (10.10) then download the LL version (10.04) as repos for 10.10 are not out yet and you wont have the libs for it.
Hopefully that helps ;)

P.S. If you in fact have PUEL alrdy then just start the VB scroll down to USB , and click on "Enable USB controller"

---

### Post by An Sanct on 2011-02-28
The 4.0 OSE edition has an extension, that enables USB (I was baffled too at first ...), but you have to download it additionally from the virtualbox site. [Quick guide]("http://www.howtogeek.com/howto/39296/virtualbox-4.0-rocks-extensions-and-a-simplified-gui/")

[direct download]("http://download.virtualbox.org/virtualbox/4.0.4/Oracle_VM_VirtualBox_Extension_Pack-4.0.4-70112.vbox-extpack") for the extension.

---

### Post by pagunston on 2011-02-28
> **An Sanct said:**
> The 4.0 OSE edition has an extension, that enables USB (I was baffled too at first ...), but you have to download it additionally from the virtualbox site. [Quick guide]("http://www.howtogeek.com/howto/39296/virtualbox-4.0-rocks-extensions-and-a-simplified-gui/")

[direct download]("http://download.virtualbox.org/virtualbox/4.0.4/Oracle_VM_VirtualBox_Extension_Pack-4.0.4-70112.vbox-extpack") for the extension.

How exactly do I install that file in Ubuntu?

---

### Post by csacpt on 2011-02-28
> **pagunston said:**
> How exactly do I install that file in Ubuntu?

This is from the manual on the Virtualbox site:

*"VirtualBox extension packages have a           .vbox-extpack file name extension.           To install an extension, simply double-click on the package file,           and the VirtualBox Manager will guide you through the required           steps."*


HTH

---

### Post by pagunston on 2011-02-28
> **csacpt said:**
> This is from the manual on the Virtualbox site:

*"VirtualBox extension packages have a           .vbox-extpack file name extension.           To install an extension, simply double-click on the package file,           and the VirtualBox Manager will guide you through the required           steps."*


HTH

When I double click the package, it opens with the Ubuntu Archive Manager. If I try to extract the file, it displays an error: An error occurred while extracting files.

---

### Post by csacpt on 2011-02-28
> **pagunston said:**
> When I double click the package, it opens with the Ubuntu Archive Manager. If I try to extract the file, it displays an error: An error occurred while extracting files.

Try opening Virtual Box Manager then File>Preferences and you should get a settings window with extensions as one of the options. Click on Extensions. There should be an add button on the right. You may have to navigate to wherever you downloaded the file.

---

### Post by pagunston on 2011-03-01
> **csacpt said:**
> Try opening Virtual Box Manager then File>Preferences and you should get a settings window with extensions as one of the options. Click on Extensions. There should be an add button on the right. You may have to navigate to wherever you downloaded the file.

Just tried this however the extensions menu does not exist. Perhaps I have a old version of virtual box?

---

### Post by csacpt on 2011-03-01
> **pagunston said:**
> Just tried this however the extensions menu does not exist. Perhaps I have a old version of virtual box?
Could be. I think the extensions is only in the latest version. The help menu should tell you which version you have.

---

### Post by An Sanct on 2011-03-01
Check version in VirtualBox in the menu under "Help" > "About"

PS. it cannot be copied, just post us the first two numbers (major and minor version ... example 3.6 / 4.0)

---

### Post by pagunston on 2011-03-01
> **An Sanct said:**
> Check version in VirtualBox in the menu under "Help" > "About"

PS. it cannot be copied, just post us the first two numbers (major and minor version ... example 3.6 / 4.0)


It is version 3.2.8_OSEr64453

---

### Post by An Sanct on 2011-03-02
Yes, that's the old version.

Download the deb package from [here]("http://www.virtualbox.org/wiki/Linux_Downloads"), uninstall the old version, install the new one.

---

### Post by pagunston on 2011-03-02
New version is now installed however when I right click the USB icon, my usb appears to be grayed out and I can not select it.

---

### Post by Habitual on 2011-03-02
**Now**, install the extension pack

---

### Post by pagunston on 2011-03-03
> **Habitual said:**
> **Now**, install the extension pack

The extension pack is installed though the USB icon is still grayed out.

---

### Post by An Sanct on 2011-03-03
Then now add yourself to the vboxusers group (mentioned in my previos post)

Here's the [link to my post #2]("http://ubuntuforums.org/showpost.php?p=10504096&postcount=2"), in case I wasn't clear enough :)

---

### Post by SilverWave on 2011-04-13
Quote:
 	 	 		 			 				 					Originally Posted by **csacpt** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10507401#post10507401") 				
 				*Try opening Virtual Box Manager then  File>Preferences and you should get a settings window with extensions  as one of the options. Click on Extensions. There should be an add  button on the right. You may have to navigate to wherever you downloaded  the file.*


Thanks! Worked a treat :-)

---

### Post by 419hookup on 2011-07-26
Well I've been messing around with this for 6 hours now so I figured I'd go ahead and register and post and see if anyone out there can help me.  I'm running a Toshiba Satellite A505 with ubuntu 11.04 and windows xp in virtualbox puel.  I've downloaded the extension packs, I've made sure that my user is included in the vboxusers and nothing works.  Still no USB.  I'm trying to hook up an ipod via VMWin.    It reads my internal camera as a usb device and I can mount it but it won't read any actual usb devices.  Is there an "off switch" I missed somewhere or a "plug" that I forgot to plug in?  Someone please tell me I'm just stupid and forgot something simple.

---

