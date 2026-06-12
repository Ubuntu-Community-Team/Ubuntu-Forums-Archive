---
title: "Map Network Drive (What is the Ubuntu Eqivalent)"
date: 2010-05-05
forum: General Help
---

### Post by michaeljwjr on 2010-05-05
I have a Belkin N+ Router that allows me to plug in my external hard drive. On windows this is easy to do because I can just map network drive and I can use it. 

What is the equivalent in Ubuntu? 

Every tutorial I have shows how to get Ubuntu to talk to windows. I don't want to talk to windows, I just want to access my drive.

---

### Post by capscrew on 2010-05-05
> **michaeljwjr said:**
> I have a Belkin N+ Router that allows me to plug in my external hard drive. On windows this is easy to do because I can just map network drive and I can use it.

What is the equivalent in Ubuntu? 

You should be able to auto mount the drive via a USB port.  It might even show up on the desktop> 

Every tutorial I have shows how to get Ubuntu to talk to windows. I don't want to talk to windows, I just want to access my drive.

You have to communicate in a windows protocol if the system is not local and is on a windows host.  If the drive is connected to the Ubuntu host via the USB port then it should automount and you should be able to find the drive in Nautilus.  From memory: it should be Places>>Computer>>Filesystem or some such.

Either way the drive has to be mounted to the local file system before you can bookmark (map) it.

---

### Post by michaeljwjr on 2010-05-05
Sorry if I wasn't clear about this I'll try again. 

My Desktop has Windows 7, and is connected to my router. My router has my External Hard Drive (Hitachi 250gb) attached to it. I mapped it to my windows machine very easily and now can access it through the router. 

I have a laptop with ubuntu on it (10.04). I want to be able to access the HD in the same manner.

---

### Post by capscrew on 2010-05-05
> **michaeljwjr said:**
> Sorry if I wasn't clear about this I'll try again. 

My Desktop has Windows 7, and is connected to my router. My router has my External Hard Drive (Hitachi 250gb) attached to it. I mapped it to my windows machine very easily and now can access it through the router. 

I have a laptop with ubuntu on it (10.04). I want to be able to access the HD in the same manner.

Ah ha.  The Windows host speaks SMB/CIFS to the drive and Ubuntu needs to do the same thing.  The package for Ubuntu to act as a SMB client is called "*smbfs *" and it may already be installed.  You still have to use the file browser (Nautilus if you have a Gnome desktop) to find the drive.  Look at Places>>Network>>  to find it.

If this doesn't work you might need to add "smbfs".  You can use Synaptics to do that.  You can filter the search to *smbfs *to find it.  Then you just select it and install.

If you are brave you can try it in the terminal (from the command line) with this: ```
sudo apt-get install smbfs
```

---

### Post by 3rdalbum on 2010-05-05
You don't need any extra software to access SMB shares. Just go to Places > Network and then you might need to double-click on Windows Network.

Also, make sure you don't have a firewall running on your client computer. It will interfere with the SMB detection, and you don't need a firewall anyway since you're behind a router.

---

### Post by michaeljwjr on 2010-05-05
@capscrew SMBFS is installed latest version (via terminal) and Nothing is popping up in Places - Network

@3rdalbum I am trying to get my laptop to see the external drive that is attached to my router. I can see it on my win7 desktop, I can see it when I plug it directly into my laptop, but I don't know how to get Ubuntu to see the external while it's attacked to the  router, windows sees it as: 

//192.168.2.1/HITACHI

How do I mount that drive in Ubuntu?

---

### Post by michaeljwjr on 2010-05-05
Progress:

I was able to go through the windows network to find the drive, but it's requiring a username/password which I haven't set on anything.

---

### Post by capscrew on 2010-05-05
> **michaeljwjr said:**
> @capscrew SMBFS is installed latest version (via terminal) and Nothing is popping up in Places - Network

@3rdalbum I am trying to get my laptop to see the external drive that is attached to my router. I can see it on my win7 desktop, I can see it when I plug it directly into my laptop, but I don't know how to get Ubuntu to see the external while it's attacked to the  router, windows sees it as: 

//192.168.2.1/HITACHI

How do I mount that drive in Ubuntu?

In the address bar of Nautilus: smb://192.168.2.1/HITACHI

Edit: Sometimes it takes a few minutes for the drive to show up in Places>>Network

---

### Post by capscrew on 2010-05-05
> **michaeljwjr said:**
> Progress:

I was able to go through the windows network to find the drive, but it's requiring a username/password which I haven't set on anything.

By this I assume that you are referring to the "*windows network*" icon in the Ubuntu file browser.

The user/pass could be the Ubuntu keyring.

FYI: The Belkin has a SMB file server built into it.  It is a Samba server.  :-)

---

