---
title: "Multiple errors after running 'update'"
date: 2010-06-27
forum: General Help
---

### Post by OxentroT on 2010-06-27
I get a list of errors after running: 
```
sudo apt-get update
```


The following errors occur after update runs:
```
Fetched 198B in 1s (184B/s)
W: GPG error: http://packages.medibuntu.org karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

What could it be? Is it that some packages haven't the need for an update? Or there is not yet any updates for some packages?:confused:

---

### Post by Brandon Williams on 2010-06-28
For the GPG warning, look back at the [instructions for adding the medibuntu repo](https://help.ubuntu.com/community/Medibuntu#Adding the Repository). I suspect that you didn't run the part of the command that installs the keyring.

For the other two warnings, the ones related to the cdrom, open the "Software Sources" dialog, click on the "Other Software" tab, and deselect any lines that start with "cdrom:". You ordinarily will not want to install from the cdrom, after all.

---

### Post by OxentroT on 2010-06-29
> For the GPG warning, look back at the instructions for adding the medibuntu repo. I suspect that you didn't run the part of the command that installs the keyring.

For the other two warnings, the ones related to the cdrom, open the "Software Sources" dialog, click on the "Other Software" tab, and deselect any lines that start with "cdrom:". You ordinarily will not want to install from the cdrom, after all. 

Thankyou for that. I will be sure and take care of these.

:guitar:

---

