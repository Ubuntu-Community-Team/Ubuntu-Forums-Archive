---
title: "No thumbnails over network resource."
date: 2011-04-29
forum: General Help
---

### Post by Roasted on 2011-04-29
I'm browsing my Samba share right now. On my pictures, they're blank and say JPG on them. I don't see the actual thumbnails. It's been like this for many releases, but only now it's irritating me to the point of wanting to find a fix.

Server is 10.10.
Laptop browsing it is 11.04.

Any ideas?

---

### Post by bobwyajnr on 2011-05-01
> **Roasted said:**
> I'm browsing my Samba share right now. On my pictures, they're blank and say JPG on them. I don't see the actual thumbnails. It's been like this for many releases, but only now it's irritating me to the point of wanting to find a fix.

Server is 10.10.
Laptop browsing it is 11.04.

Any ideas?

**Nautilus** file manager right? (Default for Ubuntu)
menus: **Edit - Preferences - Preview** - change from *Local Files Only* to *Always* as desired. No idea what's going on with Unity though. Is it the same? I'll be sticking Linux-Mint and Gnome I think...

I just noticed I get Nautilus previews whatever the value of the above setting - however I used **mount.cifs** to mount all my remote Samba shares... Might be of interest to you if are into a bit of commandline love... :)

Bob

---

### Post by Roasted on 2011-05-02
Isn't using "smb://server" using cifs?

Marking as solved - thanks for that tip!

---

### Post by bobwyajnr on 2011-05-02
> **Roasted said:**
> Isn't using "smb://server" using cifs?

Marking as solved - thanks for that tip!

Glad your problem was so easy to solve :P

**mount.cifs** will mount a Samba file share using FUSE - as userspace filesystem (like NTFS.3G). So it appears to the O.S. like a local folder. Sometimes useful for example if you try to mount a UDF/ISO disc image to loopback using the smb:// protocol (to access the CD/DVD/BluRay image) the operation will fall over (I think that might a limitation of nautilus actually). The operation *should* work when the share is mounted (**mount.cifs** or **fstab**). Still got a lot to learn myself of course!!

**mount.cifs** starts to come into it's own when you click on **nautlius - Windows Network** and get a blank screen with no files (and no feedback as to why)! **mount.cifs --verbose** (and **smbclient** for that matter) give you lots of feedback in the terminal (for troubleshooting) and finer grain control over the user being used to access the share. Worth playing about with - while you've got a working setup!


Bob

---

### Post by Morbius1 on 2011-05-02
> **Roasted said:**
> Isn't using "smb://server" using cifs?
"smb://server" is using "gvfs-mount smb://" which is a fuse thing. It will automatically create a mount point in your home directory.

mount.cifs has nothing to do with fuse but in use does have an ntfs-like syntax to it.

---

### Post by bobwyajnr on 2011-05-02
> **Morbius1 said:**
> "smb://server" is using "gvfs-mount smb://" which is a fuse thing. It will automatically create a mount point in your home directory.

mount.cifs has nothing to do with fuse but in use does have an ntfs-like syntax to it.

Ah I've still got so much to learn!! Like I still have figured out where KDE stores it's Samba server shares (setup via the Dolphin share command)... :)

Bob

---

