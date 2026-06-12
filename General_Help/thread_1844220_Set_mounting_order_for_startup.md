---
title: "Set mounting order for startup"
date: 2011-09-14
forum: General Help
---

### Post by blamerson on 2011-09-14
I'm trying to figure out how to automatically mount a looped ISO file at startup that's stored on a NFS share.  

The issue that I believe is occurring is that the NFS mount doesn't mount until after the network card is started.  The ISOs try to mount prior to the network/NFS starting and so boot hangs waiting for user input.  

The reason for this is we have a PXE boot server that mounts ISO loops for live booting.  This is so we have access to both the original ISO and the files without having to take up extra disk space by extracting the ISO.  Thanks for any help!

Brian

---

