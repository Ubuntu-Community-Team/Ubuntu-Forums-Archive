---
title: "Firefox errors on launching application  (10.10)"
date: 2010-10-16
forum: General Help
---

### Post by minimustangs on 2010-10-16
I installed Ubuntu 10.10 on a clean drive afyer an issue with 10.04 I couldn't resolve. The attched screen shot shows the error that happens when I launch Firefox. WHat is it, and how do I correct it. I can't find a setting for SSL or anything that might be turned off in firefox, so I guess it's an UBUNTU thing?

---

### Post by hhh on 2010-10-16
"The most likely cause is problems with files in your application's profile directory."

Try closing Firefox and renaming the .mozilla hidden directory in your home folder. When you restart Firefox a new one will be created. If things are fine, you can then migrate your bookmarks etc... to the new profile. More info on Firefox profiles at these links...
[http://support.mozilla.com/en-US/kb/managing+profiles](http://support.mozilla.com/en-US/kb/managing+profiles)
[http://kb.mozillazine.org/Profile_folder_-_Firefox](http://kb.mozillazine.org/Profile_folder_-_Firefox)
[http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox)

---

### Post by lovinglinux on 2010-10-17
Try deleting the files **secmod.db** and **compatibility.ini** from your profile.

---

### Post by gfi on 2010-11-16
All, the 'fix' to delete the profile works... meanwhile, does anyone know what the actual problem is with FF?

I have Cisco VPN software that relies on certificates that I import in Firefox... and because of this bug, I have to reimport my certificates every time, so that Cisco VPN can work..

---

