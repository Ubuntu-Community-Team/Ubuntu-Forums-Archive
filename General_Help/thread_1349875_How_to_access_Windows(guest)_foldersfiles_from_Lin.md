---
title: "How to access Windows(guest) folders/files from Linux(host)?"
date: 2009-12-08
forum: General Help
---

### Post by MKVCrazy on 2009-12-08
I was able to installed Windows XP on my Ubuntu using VBox OSE after 2 days of researching on how to do just that because I think my case was little uncommon and was really frustrating. But anyways I've passed that step. Now I am wondering how to access the files and folders such as "My Documents" in the guest's Windows XP system from my Ubuntu. Where are those folders located in my Ubuntu? Is this any possible?

---

### Post by 3Miro on 2009-12-08
Short answer is: you don't. 

The long answer is, you can set up a folder under Linux that windows can mount as a network drive. Then you can move files between the two systems. You need to install the virtual box guest addons (for the ose you might have them in the repository, otherwise just download them from the virtual box web-page). You basically have to go to Guest Addons -> Share folder and click on couple of places. For the details, go tothe virtual box web-page and download the manual, it is a very good manual, easy to read and follow.

---

### Post by MKVCrazy on 2009-12-08
Hi, I am not quite sure which one to download since when I search for "VirtualBox Guest Addons" the posters always mention Guest Additions. And in the ISO information page, it doesn't say clearly whether or not that addon is for dumping folder so the host and guest OS'es can share files easily. So could you verify if the one I've selected is the correct one to download?

---

### Post by 3Miro on 2009-12-08
> **MKVCrazy said:**
> Hi, I am not quite sure which one to download since when I search for "VirtualBox Guest Addons" the posters always mention Guest Additions. And in the ISO information page, it doesn't say clearly whether or not that addon is for dumping folder so the host and guest OS'es can share files easily. So could you verify if the one I've selected is the correct one to download?

The one selected on the screen-shot is the one that you need.

This is actually just in iso image, hopefully Virtual Box will automatically find it when you select "install guest addons".

The guest addons serve for more purposes than just sharing files. For example if you install them, you will no longer have to use the right ctr to move the mouse and keyboard focus. Windows will run just like any normal window under Ubuntu. There are other features for networking and USB support for the the non-ose version.

---

### Post by MKVCrazy on 2009-12-08
You mean, it's easier to do this (sharing files between host and guest) with the non-OSE version? If yes, I might reconsider giving it another try otherwise I won't. It's given me enough pain trying to find a feature that's not implemented on the program itself Lol.

---

### Post by 3Miro on 2009-12-08
> **MKVCrazy said:**
> You mean, it's easier to do this (sharing files between host and guest) with the non-OSE version? If yes, I might reconsider giving it another try otherwise I won't. It's given me enough pain trying to find a feature that's not implemented on the program itself Lol.

No, no. Sharing is implemented in the ose. The only thing that is not (as far as I know) is the USB support. You will not be able to use an USB printer directly from within the OSE version of the virtual box.

As for setting the Shard folders, it is equally easy in both versions.

---

### Post by MKVCrazy on 2009-12-10
Hi 3Miro, I've install the guest source files too. I am not sure how to exactly access those GUEST folders/files. Could you please point out?

EDIT: I've found my way to do it but I'm still kinda stuck. I get this error when I try to share one of my host folders in Ubuntu.

[IMG]http://i47.tinypic.com/2a5hfft.png[/IMG]
```
'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Memory allocation error.
```

---

### Post by MKVCrazy on 2009-12-11
Can anyone help please? :|

---

### Post by bodhi.zazen on 2009-12-11
After adding (installing) samba, log off and back on to gnome.

Then try the share again.

---

### Post by MKVCrazy on 2009-12-11
> **bodhi.zazen said:**
> After adding (installing) samba, log off and back on to gnome.

Then try the share again.
I already have **samba** and by the way I am not even sure why there are "**samba**" and "**samba4**" also. Should I uninstall the the first **samba** and keep **samba4**? Is there anything I need and not installed in the screenshot? If I recall correctly, **samba **was already installed when I first use Ubuntu Karmic and I haven't restart my PC since I installed **samba4** (installed it about 3 days ago). But just in case I'll restart my PC and report back.

---

### Post by Dennis N on 2009-12-11
Another possible solution to consider:

Transfer files between guest and host via SSH. Install openssh-server on Linux host and connect to host from XP guest with something like Filezilla for Windows. This even works with NAT mode network setup. Then you can transfer files in either direction.

---

### Post by MKVCrazy on 2009-12-11
Ok, I restarted my PC and I can now share the folders without problems :)

Problem SOLVED

---

### Post by joes7 on 2009-12-11
You must have Linux installed on one disk and Windows on the other one.

---

### Post by pricetech on 2009-12-11
Not to be argumentative, but yes you can access your virtual windows from Ubuntu.  I do it all the time.  I have the windows firewall turned off since everything here as well as at home is behind a hardware firewall.

Start by determining the IP address of your virtual winders.  From a command prompt type   ipconfig /all   and note the IP address assigned.

From Ubuntu, I use Connect to Server and point it to the IP address of the winders box.  Just for simplicity I usually just connect to the hidden C share  (c$) rather than messing with shares on the windows install.

Just that easy.

---

### Post by MKVCrazy on 2009-12-11
That seems hard but I figured out away that's easy for me :D For those who are wondering how I did. I can help with more details but below are outlines of what I did.

-installed guess additions on host (linux)
-installed guess additions on guest (windows)
-share a folder on host (linux)
-find the drive of shared folders by host on guest and put shortcut on desktop

See screenshot. Shortcut name is "Ubuntu" in the screenshot and when I click on it, I can see everything inside the shared folders by the host :)

---

