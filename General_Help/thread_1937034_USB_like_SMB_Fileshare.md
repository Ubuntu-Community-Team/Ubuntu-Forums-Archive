---
title: "USB like SMB Fileshare"
date: 2012-03-07
forum: General Help
---

### Post by Bearson on 2012-03-07
Any suggestions on how I could make an SMB file share act like an autoloaded USB device when it is auto mounted using /etc/fstab?

---

### Post by Ghost_Mazal on 2012-03-07
I don't fully understand the question.

Do you already have your share in fstab ?

Or do you want to put it in fstab ?

---

### Post by Bearson on 2012-03-07
I already have it loaded in fstab.  

What I would like is when a user logs into there account the filesystem is loaded up like a USB / External drive would load up. I would like there to be a visual showing that the drive was loaded as a removable media so they can work with the filesystem as it were a usb / external drive.

---

### Post by jerome1232 on 2012-03-07
mounting it under /media should do it


ie /media/smbshare

---

### Post by Bearson on 2012-03-07
I tried creating a folder like "/media/usersFolder" under /media.  Then loaded the smb share to "usersFolder" using fstab. I did not load automatically like a USB/external drive. Maybe because this was a created folder? Not sure why but I figured if I mounted it inside the /mount folder it would load up like a USB drive.

Should I be loading the smb share to only the root of "/mount" instead?

---

### Post by jerome1232 on 2012-03-07
> **Bearson said:**
> I tried creating a folder like "/media/usersFolder" under /media.  Then loaded the smb share to "usersFolder" using fstab. I did not load automatically like a USB/external drive. Maybe because this was a created folder? Not sure why but I figured if I mounted it inside the /mount folder it would load up like a USB drive.

Should I be loading the smb share to only the root of "/mount" instead?

It could be my information is out of date, this worked for me in the past under Gnome 2, I haven't tried it under Gnome 3 to be honest.

---

### Post by Bearson on 2012-03-07
Nope, did not work for me.  I changed the entry in fstab to mount the smb share to /media/userFolder, and then directly to the root "/media".  Both ways just loaded the file as a normal folder

---

### Post by Ghost_Mazal on 2012-03-07
I'm still confused , what exactly do you want that folder of your share to do when you say "Act like a usb drive" ?

---

### Post by jerome1232 on 2012-03-08
> **Bearson said:**
> Nope, did not work for me.  I changed the entry in fstab to mount the smb share to /media/userFolder, and then directly to the root "/media".  Both ways just loaded the file as a normal folder

I'm assuming, a) show up on the unity launcher and b) show up in the side pane of nautilus or c) show up on the desktop and places menu (under gnome2)

On my system mounting under /media works to show up in side pane of nautilus, but no go on the unity launcher.

---

### Post by Bearson on 2012-03-12
> **jerome1232 said:**
> I'm assuming, a) show up on the unity launcher and b) show up in the side pane of nautilus or c) show up on the desktop and places menu (under gnome2)

On my system mounting under /media works to show up in side pane of nautilus, but no go on the unity launcher.

Yes. to a. b. and c. 
I want the smb share to act exactly like if a usb drive is inserted into your computer.

---

### Post by Morbius1 on 2012-03-12
[1] Please stop using the term "smb" as this post does not appear to have anything to do with Samba file sharing.

[2] Like many others here I'm confused as to the nature of the problem and since it appears you have an entry in fstab why not show it's contents by posting the output of the following command:
```
cat /etc/fstab
```

---

### Post by Suparious on 2012-03-12
as long as the mountpoint exists, samba-server will just host an empty folder while the USB is **unmounted**.

As soon as you mount a USB to that folder, samba treats this as if someone just loaded files into the folder. You should see the contents visible.

Do you have any other working samba shares that prove your samba config is working?

---

### Post by bab1 on 2012-03-12
> **Bearson said:**
> I tried creating a folder like "/media/usersFolder" under /media.  Then loaded the smb share to "usersFolder" using fstab. I did not load automatically like a USB/external drive. Maybe because this was a created folder? Not sure why but I figured if I mounted it inside the /mount folder it would load up like a USB drive.

Should I be loading the smb share to only the root of "/mount" instead?

If you want the icon to appear on the desktop when a SMB (Samba) share is mounted, and you are using Gnome2, then you need to edit the GConf settings.  You can start the editor from the terminal with *[COLOR="DarkSlateGray"]gconf-editor[/COLOR]*.  It has it's own launcher under **Applications>>SystemTools **, but it may not be visible.

In any event once you have the gconf-editor open you go to **apps>nautlius>>desktop** and tick the volumes_visible box.  Then anything that is mounted under /media will noe show on the desktop.

I'm sure there is something like this in Unity or Gnome3.

---

### Post by bab1 on 2012-03-12
> **Suparious said:**
> as long as the mountpoint exists, samba-server will just host an empty folder while the USB is **unmounted**.

The mount point is on the local host.  A  mount point for any client  would not be on the Samba server.  Yes it is just a folder on the client (the local host) until the SMB resource (the share) is mounted to that local folder. > 

As soon as you mount a USB to that folder, samba treats this as if someone just loaded files into the folder. You should see the contents visible.
I believe the OP just wants the icon for the share to appear on the desktop, just as the USB stick icon appears when you plug the stick in. > 

Do you have any other working samba shares that prove your samba config is working?

---

