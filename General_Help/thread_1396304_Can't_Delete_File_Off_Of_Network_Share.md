---
title: "Can't Delete File Off Of Network Share"
date: 2010-02-01
forum: General Help
---

### Post by umechanism on 2010-02-01
I have a folder named "Gary" that I created with another computer running Windows XP.  The folder is located on an HP Media Vault (NAS).  I want to delete this folder but I can't - not even with the XP machine from which the file was created.

I've tried 
```
sudo rm -r Gary
```
but that did not do anything.  I can't seem to get rid of this darn thing.

Help!

Thanks!

---

### Post by jamesisin on 2010-02-01
I don't know how the NAS you are using handles permissions, but my first inclination is that the XP associated user is the owner and ought to have permissions to delete that file.

Are you entering that command on the NAS itself or are you trying to issue that command across a network share?

The share may not care if you are using sudo on your client system.

---

### Post by umechanism on 2010-02-02
The files were placed there off of a troubled computer that would not reboot so I used a boot CD (Hiren's Boot CD) to boot up the computer, retrieve the files, and place them on my NAS.  Hiren's uses a Windows XP environment.

The computer has been repaired so I do not have it anymore.  I am trying to remove the folder "Gary" by using Ubuntu 9.10 and browsing over to the share.

I just need an all powerful command to blow the folder away regardless of the permissions.  Something like sudo supernova delete!  :D

---

### Post by jamesisin on 2010-02-02
Can you log directly into the NAS?  Possibly using something like ssh?  Because then you could enter commands as root or superuser directly on that machine.

---

### Post by umechanism on 2010-02-02
So I went back to the computer from where I used Hiren's Boot CD and rebooted that computer using Hiren's.  I followed the same setup/steps that I previously did and gained access to the NAS.  The folder "Gary" is there.  I select it to delete it and Windows XP (mini environment within Hiren's) tells me

"Can't remove directory.  Directory is not empty".

So, I double click "Gary" to see what it inside and I get this message;

~\Gary is not accessible.  You might not have permission to use this network resource.  Contact the administrator...."

So I right-click on "Gary" to check properties and it is set to "Read Only".  I uncheck the read only mark and apply it to all folders and files inside of "Gary".  Now the properties reveal;

Size = 0 bytes
Size on disk = 0 bytes
Contains:  0 files, 0 folders.

**So I abandon Hiren's and XP and go back to Ubuntu on a different computer and check the share.  **

Here's where it gets really strange.  I show in the attached photo that "Gary" is shown to be **[COLOR="Red"]empty[/COLOR]** if I browse to it via the mount path in fstab which is
```
/mnt/hpmediavault/Volume2/Images-Vol2/Gary
```
If I use Nautilus to browse out to the share and book mark the location, then Nautilus shows it as **[COLOR="Red"]having contents[/COLOR]**.  The left half of the image is via the fstab mount path and the right half is via Nautilus.

Confused???  Me too.  Help!:-s

---

### Post by jamesisin on 2010-02-02
What is the path to the share in the right hand image?  (You can copy the real path by clicking on the pencil/paper icon to the left of the folder hierarchy.)

---

