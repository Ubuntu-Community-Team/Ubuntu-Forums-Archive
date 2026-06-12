---
title: "LibreOffice 3.4 - Fatal Error"
date: 2011-10-15
forum: General Help
---

### Post by jonbjoseph on 2011-10-15
I upgraded from Ubuntu 11.04 to 11.10 and now LibreOffice won't start.  When attempting to start LibreOffice, I get the following error:

LibreOffice 3.4 - Fatal Error
The application cannot be started
A general error occurred while 
accessing your central configuration

I tried starting LibreOffice from the toolbar and from the command line and get the same error message.  I was hoping to get a more detailed message when starting LibreOffice from the command line.

Does anyone have any suggestions on what logs I can check, or what to try in order to fix this problem?

Thanks,
Jonathan

---

### Post by jonbjoseph on 2011-10-16
LibreOffice 3.4 on Ubuntu now works on my Ubuntu 11.10 system.

I simply uninstalled LibreOffice 3.4, rebooted, then reinstalled LibreOffice 3.4

I have a feeling that all I needed to do was use the old backed up .libreoffice.bak under ~/.libreoffice after the Ubuntu 11.10 upgrade.

---

### Post by tombott on 2012-01-23
Had the same problem here, mine was a fresh 11.10 install.
If I logged in under user created during setup it worked, but not when using an additional user created after setup.
Tried removing and reinstalling but this made no difference.
In the end I checked what I should have checked to start with!

/home/user/.libreoffice was owned by root. did a chown and all was good!

```
sudo chown username:users -R /home/user/.libreoffice
```

---

