---
title: "VirtualBox PUEL USB and mouse problems after update to latest version"
date: 2011-04-29
forum: General Help
---

### Post by welshmike on 2011-04-29
I have XP running as a guest under VirtualBox. The host is Ubuntu 10.04.
After installing the update to the latest VirtualBox version, USB devices do not work and especially my USB mouse. I do not want to lose my guest XP system. I'd like to save that system, remove and reinstall the latest PUEL VirtualBox and use the saved XP guest.
Is there a way of doing this please as I do not want to have to reinstall XP, the Windows applications and rebuild what I use there? 
Please can the team help?

---

### Post by wilee-nilee on 2011-04-29
This is what you need the extension pack, to load it open virtual box click on file-preferences-extensions and load it there.
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by welshmike on 2011-04-29
Thanks for your prompt reply.
I had installed the extension pack previously. I reinstalled it and the problem is still there.
I'm considering using Acronis True Image 11 to create a backup disk image on the XP system, using VirtualBox to delete the virtual XP system, uninstalling Ubuntu VirtualBox, reinstalling it then restoring the XP image. 
I'm not sure how do the last part, but when VirtualBox gets to the point of asking what virtual system I want to create and I've replied for an XP one, VirtualBox will then want to create XP by booting from the XP install CD. I'll then insert the True Image CD and restore the XP I backed up. previously.

EDIT 1: No improvement so I saved the virtual XP machine folders VirtualBox VMs and the hidden .VirtualBox from my home folder to my desktop. I then removed VirtualBox 4.0.6 and installed the **older build 3.2.12**.
I copied back the virtual XP machine folders and started XP. **My USB mouse now works**. So Oracle have screwed USB mouse fuction. **Retraction: see my message [http://ubuntuforums.org/showthread.php?p=10738630#post10738630](http://ubuntuforums.org/showthread.php?p=10738630#post10738630)**  However USB drives are not working (no change there). 
3.2.12 is an Oracle produced virtualbox. I seem to recall that USB drives may have worked on the earlier Sun produced versions or was it Innotek versions. I will try versions earlier than 3.2.12.
EDIT 2: 3.1.8 : USB drives not supported by default.

---

### Post by wilee-nilee on 2011-04-29
I don't know but I have not seen anybody else with this problem on the forums. My usb would not work, with the latest upgrade, I installed the extensions and it did immediately. Are you getting the guest additions, and this extension mixed up? You would need both

> I'm not sure how do the last part
If this means you didn't add the extensions through the extension manager of course it didn't work. If you added the extension before the last Vbox update you didn't need them probably to get the usb to work originally. 
[ATTACH]190390[/ATTACH]

> So Oracle have screwed USB mouse fuction
Hardly.;)

---

### Post by welshmike on 2011-04-29
I think my problems are because I had VBox 3.2 and wanted to keep my installed virtual XP.
Before starting the virtual XP if I click Settings I get

Failed to access the USB subsystem 
Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {35b004f4-7806-4009-bfa8-d1308adba7e5}
Callee: 
IMachine {662c175e-a69d-40b8-a77a-1d719d0ab062}

That's possibly why I can't use USB drives but I can run virtual XP and use my USB mouse.

---

### Post by wilee-nilee on 2011-04-29
> **welshmike said:**
> I think my problems are because I had VBox 3.2 and wanted to keep my installed virtual XP.

I doubt it I have XP in virtual works fine.

The just plain vdi the machine itself will run on any virtualbox version. I just save the vdi that is all you need when changing machines.

The XP I have is the same one originally installed in vbox 3.2 and before, and upgraded to the latest vbox.

Hey if your happy with your set up now then cool, but I think the newest Vbox will run with no problems if you let somebody help you set it up correctly. 

One of the biggest problems I see on the forums are people asking for help, then doing a bunch of extra stuff beyond what is suggested in frustration, which makes it very difficult to help then, because we are not on the same page.

---

### Post by CharlesA on 2011-04-29
> **wilee-nilee said:**
> 

The XP I have is the same one originally installed in vbox 3.2 and before, and upgraded to the latest vbox.

Same here. Are you a member of the vboxusers group?

I think I had a similar issue, but it was caused by not having the extension pack installed.

---

### Post by wilee-nilee on 2011-04-29
> **CharlesA said:**
> Same here. Are you a member of the vboxusers group?

I think I had a similar issue, but it was caused by not having the extension pack installed.

No I had not really thought about it, I didn't even know there was a vbox group.

---

### Post by CharlesA on 2011-04-29
> **wilee-nilee said:**
> No I had not really thought about it, I didn't even know there was a vbox group.
I think that usergroup is only for accessing usb devices, but I am not sure.

I only started adding myself to it after my latest reinstall (about a month or so ago).

Hadn't had a problem before, but that may be because I don't use usb devices with my VMs (since they are running on a headless server).

---

### Post by wilee-nilee on 2011-04-29
> **CharlesA said:**
> I think that usergroup is only for accessing usb devices, but I am not sure.

I only started adding myself to it after my latest reinstall (about a month or so ago).

Hadn't had a problem before, but that may be because I don't use usb devices with my VMs (since they are running on a headless server).

Yeah the user groups was all you had to do before basically, and the settings-usb enabling a specific usb, beyond keyboards or mice.

The latest release a update a couple of days ago requires at least on my set up the extension in the link for usb media.

---

### Post by CharlesA on 2011-04-29
Ah gotcha. Thanks.

---

### Post by welshmike on 2011-04-30
> **wilee-nilee said:**
> I doubt it I have XP in virtual works fine.

The just plain vdi the machine itself will run on any virtualbox version. I just save the vdi that is all you need when changing machines.

The XP I have is the same one originally installed in vbox 3.2 and before, and upgraded to the latest vbox.

Hey if your happy with your set up now then cool, but I think the newest Vbox will run with no problems if you let somebody help you set it up correctly. 

One of the biggest problems I see on the forums are people asking for help, then doing a bunch of extra stuff beyond what is suggested in frustration, which makes it very difficult to help then, because we are not on the same page.
Yes, I'm guilty of trying to do it myself and doing extra stuff before I knew what is suggested by those who have been successful.
Hence my starting message [http://ubuntuforums.org/showthread.php?p=10736244#post10736244]("http://ubuntuforums.org/showthread.php?p=10736244#post10736244") in this thread.
I'd appreciate being told how to start again given that I currently have a working 4.0 with a working USB mouse but no working other USB devices.
So what is the process please?
e.g. What do I need to save from the VirtualBOX VMs folder and the hidden .Virtualbox folder before uninstall and reinstall of 4.0 followed by enabling the extension pack and guest additions.

---

### Post by welshmike on 2011-05-07
Well I decided, **** it, there were only two Windows apps I needed to run on my guest XP. So I deleted the guest and all files that Vbox used for it. 
I uninstalled Vbox and installed Version 4, ensured that the extension packages were enabled, installed guest Windows XP, guest additions and the 2 apps, one of which was Works for its database.
Everything is now working OK: USB devices, CD/DVD, Shared folder, etc.

---

### Post by CharlesA on 2011-05-08
Glad you got it working. :)

Don't forget to mark the thread as solved from Thread tools.

---

### Post by RainKap on 2011-05-12
I was tearing my hair out last night; I had similar problems with USB: my USB scanner, which had worked fine up to v4.0.4, had stopped, and I found that the USB subsystem was dead for Virtualbox. I followed the advice of enabling both users on my system in the vboxusers group, whereupon the USB subsystem woke up for Virtualbox, *but* the mouse no longer worked! When I started up the Windows XP guest, the mouse cursor just sat where it happened to be when I started the Windows VM. Installing the latest flavour of the Virtualbox extensions didn't help either; however this morning I thought to try disabling the USB filter for the mouse in Virtualbox, and bingo, the mouse was working again in the guest OS. With luck, this may help anyone who hits a similar problem...

Ian

---

### Post by welshmike on 2011-05-12
Yes. Similar near baldness for me. Very frustrating hence complete reinstall of V4 and XP.

---

