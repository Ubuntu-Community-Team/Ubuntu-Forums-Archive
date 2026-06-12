---
title: "Execute program from external NTFS drive"
date: 2010-10-25
forum: General Help
---

### Post by sojyujai on 2010-10-25
I'm trying to set up a USB thumbdrive as a password manager using the "Lastpass Pocket" portable app for Ubuntu.  I want to be able to access the thumbdrive from Windows machines as well so I formatted it with NTFS.

Lastpass Pocket runs fine from my Ubuntu computer but when I transfer it to the thumbdrive it loses its execute permission and fails to run.  I've tried giving it execute permission with no success.

I'm guessing this is a problem with the lack of linux permissions in NTFS filesystems.  I seem to remember that in older versions of Ubuntu files on an NTFS drive would all have execute permission - previously when you double clicked on a simple text file you would be asked if you would like to display or execute the file.  That doesn't seem to happen anymore, at least not on my install of Maveric.  

Did Ubuntu change the default permissions for automounted NTFS drives?

I think I could set execute permission on an internal NTFS drive within /etc/fstab but I have no idea how to do it with a removable drive.

Is there any way to change execute permissions for a removable NTFS drive? (ie. to make all files executable like how it used to be?)

---

