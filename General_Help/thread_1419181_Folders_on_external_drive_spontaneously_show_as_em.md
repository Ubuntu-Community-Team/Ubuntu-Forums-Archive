---
title: "Folders on external drive spontaneously show as empty until remount"
date: 2010-03-01
forum: General Help
---

### Post by feelsbad on 2010-03-01
I'm completely new to linux, but I'm trying. I'm running 9.10 64 bit. 

I have an external NTFS drive connected with firewire. Sometimes a large number of folders on the drive start showing as empty, and I lose access to anything in those folders. I keep my mp3s on that drive, so I usually notice it when my music player craps itself. If I unmount then remount the drive, everything works again. 

I haven't lost any data as far as I can tell, but the system is hard to use until I kill whatever process is trying to read from the drive when this happens. 

Any thoughts?

---

### Post by quixote on 2010-03-03
It sounds like something is somehow changing the permissions on the folders on the fly.  To check whether that's the case either use "ls" in a terminal, if you're comfortable with that, or check those directories using nautilus.  Select "list" instead of "icon" view, and make sure that the preferences under View > Visible Columns are set to show "Owner" and "Permissions".  When you cannot see the contents, who's listed as the owner of that directory, and what are the permissions (the rwx-rw-rw bit) ?  When you can see them, what does it say?

---

