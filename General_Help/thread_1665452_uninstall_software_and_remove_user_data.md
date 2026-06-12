---
title: "uninstall software and remove user data"
date: 2011-01-12
forum: General Help
---

### Post by kenzen on 2011-01-12
Hi, I was making some tests and I could see that ubuntu software management systems doesn't delete user data when uninstalling applications, only the binary packages.

e.g. reinstalling Thunderbird won't delete the email accounts info.

Is this supposed to be like this?

Thanks.

---

### Post by James_Lochhead on 2011-01-12
Applications store things like this in a hidden folder in your home directory. Folders like this are generally hidden by putting a dot in front of their name, for example, .thunderbird/. To delete your settings simply delete that folder.

If you're using Nautilus (the GNOME file manager which is the default in Ubuntu) you can see hidden folders by pressing ctrl + h.

---

### Post by West201 on 2011-01-12
In most cases Yes.

I found this link. Its I'm sure it'll help :) 

[http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07](http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07)

---

### Post by kenzen on 2011-01-12
thank you, very informative link. however, I can't see which of these instructions allows me to delete orphan user data files.

package system seems to be aware only of the dependencies of the binary packages, but not the user data. And this is ok, because each application may generate different kind of user data in different locations during its "life" so it would be a waste of resource to keep track of these changes, BUT, shouldn't we have a way to uninstall an application including the generated user data? something like:

1) ask application for user-data removal (this should be up to every app)
2) uninstall/remove binary packages (including dependencies, as usually)

---

### Post by kenzen on 2011-01-12
*duplicated message*

---

### Post by kenzen on 2011-01-12
*duplicated message*

---

### Post by oldos2er on 2011-01-12
Use *apt-get purge <package>* to remove user config/data files.

---

### Post by West201 on 2011-01-12
You could also use Synaptic Manager, and select the package you want to uninstall and select Complete Removal.

---

### Post by ankspo71 on 2011-01-12
> **kenzen said:**
> Is this supposed to be like this?

I think it is intended to be this way to prevent accidental removal of personal (or otherwise important) user data, such as passwords, emails, bookmarks, photos, videos, contacts, and so on, that are stored in those hidden application's user settings folders in your home folder. I always have to delete those folders by hand. These particular folders generally aren't created during the installation process anyways because the application itself creates them when they are run for the first time.

Not even using "sudo apt-get purge <package>" or "mark for complete removal" (in synaptic) will delete those particular hidden application settings folders in my home folder (Unless something has change while I was away from Ubuntu for a while). I believe these special removal options are  meant to remove the configuration files, symlinks, scripts, and other settings (eg: settings for 'all users') that were created or installed during the installation of the package, most of which aren't located in the home folder.

---

