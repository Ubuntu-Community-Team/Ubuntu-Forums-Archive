---
title: "smb shares not browsable under applications ?"
date: 2009-07-20
forum: General Help
---

### Post by dkbk on 2009-07-20
Hi all

I've set up a windows network share with smb client and I'm using automount (using gvfs) so its accessible at startup.  The mount point appears on the desktop and under places as it should.

However, the shares don't appear when I'm inside an application (for example OOo 3.0 or zimbra desktop 1.0).  OOo doesn't even use the places image so I have no idea where to go from there.  As for zimbra desktop, it uses places but its not under the places items for some reason.

Since my fileserver is a windows computer, that's a bit of an issue.

Is there a way to make those shares appears in applications ?  I've tried to use links but the programs recognize them as files only.

Thanks.

PS : Using Ubuntu 9.04.  Is this a 9.04 bug or samba's usual behavior?

---

### Post by doas777 on 2009-07-20
well, your probably going to have to use smbclient to mount the share to a system mountpoint rather than a userspace one (gvfs), in order to acheive that end. you may be able to navigate to ~/,gvfs to find it, but I've never been sucessfull in scripting access to the mounts within it.

---

### Post by dkbk on 2009-07-20
Thanks for the reply.

Do you mean using fstab to mount to share at startup such as in this tut : "https://help.ubuntu.com/community/MountWindowsSharesPermanently" ?

As you may be able to tell this is all fairly new to me and I pick things up as I go along.

---

### Post by doas777 on 2009-07-20
the linked guide is one way to do it (though it may be overkill for your usecase), or you could just mount the shares on demand from a smbclient script. ultimately you need to get the share mounted to a point on the disk (but not ~/.gvfs) so you can address it.

I used to have to do the same thing in dos, since it wouldn't read UNC paths. used 'net use' to make a mount, accessed it by drive letter, then destroyed the mount when i was done.

---

### Post by dkbk on 2009-07-21
the fstable method outlined above was surprisingly easy and straightforward and automounts at startup perfectly.
 
I only had to change the servername for the ip adress (it had a static ip anyway) and synched it in the documents folder and it works perfectly.
 
thanks for the info about the limitations of gvfs.

---

