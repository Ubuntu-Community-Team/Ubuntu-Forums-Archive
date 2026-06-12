---
title: "accessing files on another (Mac) system"
date: 2012-03-15
forum: General Help
---

### Post by mzimmers on 2012-03-15
Hi -

I've seen a lot of how-tos about sharing files on ubuntu with other machines. I'd like to go the other way, and access files on my Mac from ubuntu 11.10. 

The Mac side is already prepared (I can get to files there from my Windows box). Can someone tell me what I have to do on ubuntu? All I want is a desktop icon with a link to the shared folder on the Mac, and that will suffice for now.

Thanks...

---

### Post by mzimmers on 2012-03-18
BTT.

My needs are modest (I think): I just want to be able to see some folders on my Mac, using AFP or SMB. Any suggestions? Thanks.

---

### Post by HiImTye on 2012-03-18
if you can get to them from nautilus (i.e. from Network) then you can make a samba shortcut to it, such as:
smb://C/Shared
would go to the samba computer 'C', in the share 'Shared'

Im not sure if the same sort of thing works for apple's file sharing protocol as I don't actually have any macs to test it out on

---

### Post by mzimmers on 2012-03-18
That might be an option. On the subject of nautilus, my only use of it comes from launching through a terminal window. Is it available through the GUI? When I use "Dash home" to search for it, I don't find anything.

After a bit more experimentation, I discovered that I can get to my Mac by browsing the network. Now, I'd like to make a link (to put in Launcher or my desktop) that takes me directly to the desired location. But, apparently that's not an option with AFP connections (or so the error box tells me).

I think I'm getting close; I'm just looking for something convenient (like a link on my desktop.)

---

### Post by mikejonesey on 2012-03-18
i think maybee what you are looking for is to mount the mac book drive?

as you are using samba...
```
mount -type smbfs -o username=domain\username,password=**** 10.0.0.25:/c$/ /mnt/local/mount
```

you can then enable mounted locations to show on desktop or add a sym link to loc, then add the mount to fstab...

---

### Post by mzimmers on 2012-03-18
This looks like an interesting possibility, though I'm still looking for something more...easy to use, I guess. It appears that I have network access to the Mac (as indicated in my file browser), so I'm just looking for an easier way to get to a specific location.

As an analog, in Windows 7, I navigate to the desired network location, and just create a link. I put the link on my desktop, and when I double-click, it opens a window to the location. Surely there's an equivalent in ubuntu?

---

### Post by HiImTye on 2012-03-18
its much easier to call the share by computer and name, using nautilus, let it do all the work for you, i.e.
```
nautilus "smb://C/Shared"
```will mount it in .gvfs (although it will only be available to the current user, until the other user mounts it, but most people only have one active user anyway)

you can make this a bash script and put it on your desktop
```
#!/bin/bash
nautilus smb://C/Shared
exit
```it can then be referenced at "~/.gvfs/<Share> on <Computer>/"

or you can do it the way that mikejonesey suggests, making sure to add gksudo or run it in a shell with sudo

you can also do it manually, in Nautilus, using 'Network' on the left hand pane (using the 'Places' view)

---

