---
title: "Why does open office not have the Base application installed by default?"
date: 2010-01-27
forum: General Help
---

### Post by trevorlewis on 2010-01-27
I am a complete newcomer to Ubuntu (or Linux in general for that matter) although I have many years' experience of Windows. It seems to me that the Base application of the open office suite of programs has not been installed by default. Why is this? And how do I install it in Ubuntu 9.1?

Edited 28 Jan:
Thank you for the responses: I have run the sudo commands suggested and all is now well.

---

### Post by michy99 on 2010-01-27
I assume it is because most users don't need it. To install, open a terminal and enter```
sudo apt-get update && sudo apt-get install openoffice.org-base
```Or search for openoffice.org-base in Synaptic Package Manager if you prefer to install that way.

---

### Post by warfacegod on 2010-01-27
> **trevorlewis said:**
> I am a complete newcomer to Ubuntu (or Linux in general for that matter) although I have many years' experience of Windows. It seems to me that the Base application of the open office suite of programs has not been installed by default. Why is this? And how do I install it in Ubuntu 9.1?

It's likely that it doesn't install by default because of size issues for a CD install disc. Only 700 MB after all.

Go to: System> Admin.> Synaptic> search for openoffice.org-base> Mark For installation> Apply

---

### Post by Keith Sayers on 2010-04-11
> **michy99 said:**
> I assume it is because most users don't need it. To install, open a terminal and enter```
sudo apt-get update && sudo apt-get install openoffice.org-base
```Or search for openoffice.org-base in Synaptic Package Manager if you prefer to install that way.

	I have encountered the same problem in moving from Suse to Ubuntu 9.10.  I tried that line of code but got two screens of what seemed to mainly be error messages ending with :
Package openoffice.org-base is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source.  However the following packages replace it:
  openoffice.org-common openoffice.org-base-core
E: Package openoffice.org-base has no installation candidate

	So I added the -core bit and tried again with a similar result ending in :
openoffice.org-base-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

	I was not sure what that meant but when I went back to Applications &#8211; Office  Base was not listed with the other OO packages.  I then tried this Synaptic Package Manager but the only database offered there was MySQL.  Could anyone suggest how I could get Base up and operating, please?

---

