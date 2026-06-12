---
title: "how do you scan for viruses on a network location"
date: 2010-04-07
forum: General Help
---

### Post by X1R1 on 2010-04-07
How can i do this? I have both clamav and Bitdefender scanner for unices and I need to scan a shared folder, but it seems none of the AV programs understand samba dirs (ie. smb://compname/sharedfolder/)

Is there a way to do this?

regards

---

### Post by dcstar on 2010-04-07
> **X1R1 said:**
> How can i do this? I have both clamav and Bitdefender scanner for unices and I need to scan a shared folder, but it seems none of the AV programs understand samba dirs (ie. smb://compname/sharedfolder/)

Is there a way to do this?

regards

Mount the network shares in your fstab file and then you should be able to access them as any other folder.

---

### Post by X1R1 on 2010-04-07
How do you specify a network location of Fstab? can you put sintax here please?

thank you for your help

---

### Post by 3rdalbum on 2010-04-07
> **X1R1 said:**
> How can i do this? I have both clamav and Bitdefender scanner for unices and I need to scan a shared folder, but it seems none of the AV programs understand samba dirs (ie. smb://compname/sharedfolder/)

Is there a way to do this?

regards

Go to Places > Network and mount the share (or Places > Connect to Server...) so it is on your desktop.

The share will actually be mounted to **a folder inside** ~/.gvfs - that is, a folder inside a hidden folder called .gvfs, inside your home directory.

Your antivirus program will be able to scan all mounted shares by scanning ~/.gvfs, or a single share by scanning the subfolder.

---

### Post by X1R1 on 2010-04-07
3rdalbum, 

I did found that out after I tried to scan with clamav (on the results window that ".gvfs" folder appeared.

So I tried as you suggested but the antivirus (doesnt matter which one) crashes after I told him to scan the location.

Bitdefender scanned only 3 files (founded 3 viruses lol) and then ended the scan (the share is a full hard drive).

Clamav "grays out" as soon after I give the start command on clamgtk interface.

Is this a problem regarding the antivirus or the network share?

---

