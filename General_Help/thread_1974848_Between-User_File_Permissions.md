---
title: "Between-User File Permissions"
date: 2012-05-06
forum: General Help
---

### Post by cmat on 2012-05-06
Hello UF,

I have had no luck setting up the following configuration on my Ubuntu 12.04 machine. I have a directory that users can copy files over to work on. I want to setup the permissions in such a way so they cannot edit or delete the files at their source, but they become the owner once they copy the data over to their home folder (or any directory that they own). As a last ditch attempt I set the soruce directory's permissions to be very permissive yet, when I copy files over to a user account the folder is ediatable (I can delete or rename it) but the files within are 'locked'.

Additional information: The directory is mounted as a Samba drive, which is configured to use the user 'nobody'. The folders themselves are owned by root as of now.

Thanks

---

